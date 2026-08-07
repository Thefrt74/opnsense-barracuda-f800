# 05 — Network and interfaces

This is the most useful chapter of the whole guide. The labels printed on the chassis do **not** match the order OPNsense enumerates the interfaces in, and that mapping is almost impossible to find online. Once you've worked it out for your unit, write it down here — it's the single thing other people will come to this page for.

## Interface naming on FreeBSD

OPNsense is built on FreeBSD, so interfaces are named after their driver, not by a friendly "eth0" scheme:

| Driver | Hardware |
|---|---|
| `igb` | Intel 1 GbE (i210 / i350 family) |
| `ix` | Intel 10 GbE SFP+ (82599 / X520 family) |
| `em` | Intel 1 GbE (older 8254x family) |

So a copper gigabit port shows up as `igb0`, `igb1`… and an SFP+ port as `ix0`, `ix1`…

<!-- TO FILL: confirm which drivers actually appear on your F800.
     You can read them at the console with `ifconfig` or in the web UI
     under Interfaces > Overview / Assignments. -->

## Physical port → interface mapping

**This is the table that matters.** Fill it in for your unit.

| Chassis label | OPNsense interface | Type | Driver | Assigned role |
|---|---|---|---|---|
| <!-- e.g. p1 --> | `igb0` | 1 GbE copper | `igb` | WAN |
| | `igb1` | 1 GbE copper | `igb` | LAN |
| | `ix0` | 10 GbE SFP+ | `ix` | |
| | `ix1` | 10 GbE SFP+ | `ix` | |
| | | | | |

### How to build this table

Enumeration order rarely follows the chassis print, so map it empirically:

1. At the first-boot console, decline auto-assignment so you can watch link state.
2. Plug a **single** cable into one physical port.
3. Run `ifconfig` (console) or open **Interfaces > Overview** (web UI) and note which interface shows `status: active`.
4. Label that port, unplug, move to the next port, repeat.

Do them one at a time — plug everything in at once and you can't tell which is which.

## SFP+ ports

The four SFP+ cages are the reason this box is worth buying.

<!-- TO FILL:
     - which SFP+ modules were recognised (brand + part number)
     - which were rejected — Intel NICs sometimes refuse non-Intel optics
     - DAC (direct-attach copper) cables: worked or not?
     - link speed negotiated (10G? did it fall back to 1G?)
     - did you need to force media/speed anywhere? -->

> Intel `ix` controllers have a history of refusing third-party optics unless a kernel tunable is set. If you hit this, note the exact tunable that fixed it — that alone is worth the page.

## Assigning interfaces

At first boot, OPNsense walks you through assigning WAN and LAN.

<!-- TO FILL:
     - which physical port you chose for WAN, which for LAN
     - whether you set up VLANs at this stage
     - the console assignment dialog, briefly -->

## Base configuration

<!-- TO FILL — GENERIC VALUES ONLY. Your real addressing plan, firewall
     rules and VPN config belong in a PRIVATE repo, never here.
     Safe to document:
     - WAN: DHCP or static (describe the method, not your real IP)
     - LAN: subnet used (use documentation ranges like 192.0.2.0/24)
     - VLAN approach in principle, not your real VLAN IDs
     - DHCP server, DNS resolver — settings, not secrets -->

## Network diagram

<!-- Generic / anonymised version only. -->

![Network diagram](assets/network-diagram.png)

---

Next: [Plugins](06-plugins.md)
