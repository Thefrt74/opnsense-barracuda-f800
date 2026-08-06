# OPNsense on Barracuda F800

Complete documentation for installing and configuring **OPNsense** on a repurposed **Barracuda NextGen Firewall F800** appliance.

> These appliances now sell cheap on the second-hand market. Under the hood they are plain x86 servers — nothing stops you from running a free operating system on them. Online documentation, however, is scarce and scattered. Hence this repository.

Why this box?

€150 on eBay. For that price you get DDR4 memory, 12 threads and four SFP+ ports — nothing else in that range comes close. The only catch is the vendor firmware, and that's what OPNsense is for.

Good to know: there is no proprietary hardware inside — Intel NICs, an AMI BIOS and an Intel CPU. It's a standard x86 server in a firewall chassis.

---

## The hardware

| Item | Value |
|---|---|
| Model | Barracuda F800 (revision `F CCE` — *confirm on your own unit*) |
| CPU | Intel Xeon E5-2620 v3 |
| RAM | 24 GB DDR4 |
| Networking |Intel i350 Copper ports + Intel X710 SFP+ ports |
| Storage | SATA drive |
| Console | Serial port (no usable video output at boot) |

## Contents

| Chapter | Topic |
|---|---|
| [01 — Hardware](docs/01-materiel.md) | Specifications, teardown, storage, things to watch out for |
| [02 — Serial console access](docs/02-acces-serie.md) | Cabling, terminal settings, first steps |
| [03 — BIOS](docs/03-bios.md) | Entering the BIOS, boot order, serial redirection |
| [04 — Installing OPNsense](docs/04-installation.md) | Installation media, procedure, pitfalls |
| [05 — Network and interfaces](docs/05-reseau.md) | Mapping physical ports to system interfaces |
| [06 — Plugins](docs/06-plugins.md) | CrowdSec and other installed extensions |
| [07 — Troubleshooting](docs/07-depannage.md) | Problems encountered and how they were solved |

## Status

🚧 Documentation in progress.

## Disclaimer

Repurposing a proprietary appliance voids any warranty and vendor support. The steps described here permanently wipe the original system. Proceed at your own risk.

This project is not affiliated with or endorsed by Barracuda Networks or Deciso (OPNsense).

## License

See [LICENSE](LICENSE).

## Contributing

Feedback, corrections and additions are welcome — open an issue or a pull request.
