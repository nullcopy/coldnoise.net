+++
date = '2026-03-22T12:00:00-06:00'
draft = false
title = 'YubiKey 2FA Full-Disk Encryption for NixOS'
tags = ['NixOS', 'security', 'YubiKey', 'LUKS', 'tutorial']
+++

This guide walks through setting up YubiKey-based full-disk encryption on
NixOS. You'll end up with a system that requires both your YubiKey and a
password to decrypt and boot. I'll also walk through how to register a fallback
Yubikey, in case your primary key gets lost or damaged.

## Why YubiKey + LUKS?

Standard LUKS encryption protects your data with a password. Adding a YubiKey
can enable two-factor authentication to unlock your system. This means an
attacker would need both something you know (password) and something you have
(the physical key) to gain access. Even if someone discovers your password,
they can't decrypt your drive without the YubiKey.

The NixOS `boot.initrd.luks.yubikeySupport` module handles this integration,
but the upstream version had some issues that made backup keys impossible. A
[pending PR](https://github.com/NixOS/nixpkgs/pull/499335) fixes these problems
by disabling salt rotation and storing the cryptographic salt in your NixOS
configuration rather than on a separate file that could get corrupted

## Installation Guide
### What You'll Need

- A NixOS installation ISO (booted and ready)
- One or more YubiKeys with an available HMAC-SHA1 slot
- A target disk to install NixOS on

### Step 1: Boot the NixOS Installer

Boot from your NixOS installation media. You'll need network access to clone
the setup scripts.

### Step 2: Clone the Setup Tools

```bash
git clone https://github.com/nullcopy/ykluks-tools.git
cd ykluks-tools
```

### Step 3: Run the Setup Script

The setup script handles everything to prepare your disk for NixOS
installation: partitioning, LUKS encryption, YubiKey configuration, and
LVM/btrfs setup. You must specify which disk you wish to install on.

```bash
./scripts/ykluks-setup.sh /dev/nvme0n1
```

Replace `/dev/nvme0n1` with your target disk.

> **WARNING! This will permanently erase all content on the disk.**

The script will:

1. Ask for your target unlock time. Longer is more secure.
2. Partition the disk (256MB EFI + encrypted root)
3. Configure your YubiKey's HMAC-SHA1 slot
4. Prompt for your LUKS password
5. Create LVM volumes (swap + root) with btrfs
6. Generate a `yubikey-luks.nix` configuration file

When prompted for your YubiKey, insert it and touch the button when it blinks.

### Step 4: Generate NixOS Configuration

The LUKS partition has now been configured. It is unlocked and ready for you to
install your operating system. First, setup your nixos configuration. Be sure to 
edit `/mnt/etc/nixos/configuration.nix` according to your installation needs.
More information can be found on the [NixOS wiki](https://nixos.wiki).

```bash
nixos-generate-config --root /mnt
```

### Step 5: Import the YubiKey Module

The setup script created `yubikey-luks.nix` in the current directory. Copy it
to your NixOS configuration. This configuration enables the bootloader to find
the LUKS partition, and unlock it with your Yubikey and password.

```bash
cp yubikey-luks.nix /mnt/etc/nixos/
```

Edit `/mnt/etc/nixos/configuration.nix` and add the import:

```nix
{ config, pkgs, ... }:

{
  imports = [
    ./hardware-configuration.nix
    ./yubikey-luks.nix # <--- ADD THIS LINE
  ];

  # ... rest of your configuration
}
```

> Note: At time of writing, this configuration uses my version of the luksroot
> module. It has not been reviewed by a third party, and I provide no warranty
> for its use. I will update this post if/when the module has been reviewed and
> merged to nixpkgs, and can be recommended for general use.

### Step 6: Install NixOS

```bash
nixos-install
```

When complete, reboot. You'll be prompted to insert your YubiKey and enter your
password.

## Adding a Backup YubiKey

Once you're booted into your new system, you can register additional YubiKeys.
This is the whole reason I [modified the upstream
module](https://github.com/NixOS/nixpkgs/pull/499335)—the original design made
backup keys impossible. You can do this at any time, in case you lose a key and
need to register a new one.

```bash
git clone https://github.com/nullcopy/ykluks-tools.git
cd ykluks-tools
sudo ./scripts/ykluks-addkey.sh
```

The script will:

1. Authenticate using your existing YubiKey + password
2. Prompt you to insert and configure the new YubiKey
3. Set a password for the new key (can be the same or different)
4. Register the new key with LUKS

Now either YubiKey can unlock your system.

## How It Works

The YubiKey doesn't store your LUKS key directly. Instead:

1. You enter a password
2. The password is sent to the YubiKey as a challenge
3. The YubiKey computes an HMAC-SHA1 response using its secret key
4. The response is run through PBKDF2 to derive the actual LUKS key

This means the same password produces different LUKS keys on different
YubiKeys. Each YubiKey has its own LUKS key slot, which is why you can have
multiple keys registered.
