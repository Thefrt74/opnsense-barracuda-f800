# 07 — Troubleshooting

A running log of problems and their fixes. Format: **symptom → cause → fix**. Write everything down, even what feels obvious now — this is the page someone lands on at 2 a.m. when nothing works.

---

## Garbled characters on the serial console

**Symptom:** the terminal shows random symbols instead of readable text.

**Cause:** wrong baud rate. The cable and adapter are fine — the speed is mismatched.

**Fix:** the Barracuda BIOS runs at **19200**; OPNsense runs at **115200**. Match your terminal to whichever stage you're at. See [Serial console access](02-serial-console.md).

---

## Nothing at all on the serial console

**Symptom:** completely blank terminal, no output at any speed.

**Possible causes:**
- USB-to-serial adapter not recognised by the host
- wrong cable type
- connected too late (some appliances only emit during a short window at power-on)

**Fix:**

The CH340 adapter needed Linux to be recognised on this build 

---

## Installer disk not detected

**Symptom:** the OPNsense installer doesn't see the SATA drive.

**Cause:** SATA controller in the wrong mode in the BIOS.

**Fix:** set SATA mode to **AHCI** in the BIOS. See [BIOS](03-bios.md).

---

## Appliance boots back into the installer

**Symptom:** after installation it keeps launching the installer.

**Cause:** the USB stick is still plugged in, or the boot order still lists USB first.

**Fix:** remove the stick, and set the internal drive first in the boot order.

---


---

## <!-- next problem -->

**Symptom:**

**Cause:**

**Fix:**

---

## Starting over

