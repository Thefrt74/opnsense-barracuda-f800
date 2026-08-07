# 05 — Network and interfaces

This is the most useful chapter of the whole guide. The labels printed on the chassis do **not** match the order OPNsense enumerates the interfaces in, and that mapping is almost impossible to find online. Once you've worked it out for your unit, write it down here — it's the single thing other people will come to this page for.

## Interface naming on FreeBSD

OPNsense is built on FreeBSD, so interfaces are named after their driver, not by a friendly "eth0" scheme:

| Driver | Hardware |
|---|---|
| `igb` | Intel 1 GbE (i210 / i350 family) |
| `ix` | Intel 10 GbE SFP+ (82599 / Intel X710 ) |
| `em` | Intel 1 GbE (older 8254x family) |

So a copper gigabit port shows up as `igb0`, `igb1`… and an SFP+ port as `ix0`, `ix1`…

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


> Intel `ix` controllers have a history of refusing third-party optics unless a kernel tunable is set. If you hit this, note the exact tunable that fixed it — that alone is worth the page.

## Assigning interfaces

At first boot, OPNsense walks you through assigning WAN and LAN.
 Default ports is **ixl0** and **ixl1**

!! If you want modify the interface

Go on the serial console

login
and click on 1 to assign interface and change it

---

Next: [Plugins](06-plugins.md)
