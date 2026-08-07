# 04 — Installing OPNsense

At this point you should have a working serial console ([chapter 02](02-serial-console.md)) and a BIOS set to boot from USB ([chapter 03](03-bios.md)). This chapter covers writing the installer, booting it, and getting through the installation itself.

## Version installed

| Item | Value |
|---|---|
| OPNsense version | last version works ( 26.7.1 )  |
| Image type | serial  |
| Architecture | amd64 |

> **Use the `serial` image, not `vga`.** With no usable video output, a `vga` image leaves you staring at a frozen screen with no way to interact. The `serial` image sends everything over the console at 115200 baud.

## Downloading the image

Get the image from the official mirror list: <https://opnsense.org/download/>

- Architecture: **amd64**
- Image type: **serial (Serial Console)** — not VGA, not Nano
- Verify the download against the published checksum before writing it.

I use default mirror by opnsense.

## Writing the USB stick

The image comes compressed (`.img.bz2`) and must be decompressed first.

### Linux / macOS

```bash
# Decompress
bzip2 -d OPNsense-XX.X-serial-amd64.img.bz2

# Identify the target device — CHECK THIS CAREFULLY before writing
lsblk                        # Linux
diskutil list                # macOS

# Write it (replace sdX / diskN with your actual device)
sudo dd if=OPNsense-XX.X-serial-amd64.img of=/dev/sdX bs=1M status=progress conv=fsync   # Linux
```

> ⚠️ `dd` writes to whatever device you name, with no confirmation. Point it at the wrong disk and you wipe it. Double-check with `lsblk` / `diskutil list` that you have the USB stick and not your system drive.

### Windows

Use **Rufus** or **balenaEtcher**. Etcher handles the `.bz2` directly; with Rufus, decompress first with 7-Zip. Select the image, select the USB stick, write.

## Booting the installer

1. Plug the USB stick into the appliance.
2. Have the serial console open at **115200 baud** (the OPNsense image speed — not the 19200 you used for the Barracuda BIOS).
3. Power on. Enter the boot menu or let the changed boot order pick up the USB stick.

Wait a moment while OPNsense boots. Once it's done, you're in the OPNsense serial installer.

## Running the installer

The live system boots to a login prompt.

1. Log in with the installer account:
   - user: `installer`
   - password: `opnsense`
2. The installer starts automatically.
 and you can configure
set your password with the root user
set your raid option ( mirror, stripe)

### UFS or ZFS?

For this build I chose ZFS. It's more resilient against data corruption, and its snapshot feature lets you roll back a bad change. Snapshots use a bit more RAM, but with 24 GB on this machine that's a non-issue.

## First boot

Remove the USB stick after the reboot (or the appliance may boot back into the installer).

The system comes up to the console menu and asks you to assign interfaces. This is where the physical-port-to-interface mapping matters, and it has its own chapter: [Networking](05-networking.md).

-assigning WAN / LAN at the console
-the default LAN IP the system lands on
-(default is https://192.168.1.1, user root, the password you just set) -->


---

Next: [Networking and interfaces](05-networking.md)
