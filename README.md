# Reactor Dissection
 
**An interactive, single-file explorer for how nuclear reactors are put together.**
 
Reactor Dissection is an educational tool for an introductory course in fission reactor technology. Like a biology dissection, it lays the parts of a nuclear plant out so students can see how they fit and why they are made the way they are: 2D system drawings layered by system and physical property, 3D cutaway models, a common-scale comparison, and drill-down from containment structures to seals and bolts.
 
Current version: **1.9**
 
> **Please read.** This tool and its data are intended for **education**. All dimensions, operating values and descriptions come from **public sources** and are representative. Many are approximate and must be checked against the plant-specific FSAR or DCD before being cited or used for any engineering purpose. The software and information are provided "as is", without warranty of any kind.
 
## Quick start
 
1. Download `Reactor_Dissection_v1_9.html`.
2. Open it in a current desktop browser (Chrome, Edge, Firefox or Safari).
That is the whole installation. There is no build step, server or account. The 3D library is included in the file, so the tool works offline; only the display font is loaded from the web, with a system-font fallback.
 
To host it with GitHub Pages, rename the file to `index.html` (or link to it from one) and enable Pages for the repository.
 
## What it does
 
| View | What you see |
|---|---|
| **2D systems** | Piping, equipment, instrumentation and structural boundaries for one reactor. Toggle layers, pan, zoom, click anything to inspect it. A flat drawing or an isometric half-section. |
| **3D dissection** | A 3D model with cutaway sliders on three axes, transparency, explode-by-system, orthographic or perspective camera, optional landscape, and binary STL export for 3D printing. |
| **Scale comparison** | Every reactor at one scale beside a person and the Statue of Liberty. |
| **Side by side** | Two full system drawings at one scale. |
| **Art** | Links to historical reactor wall charts and cutaway posters, plus a place to attach your own images. |
 
Other features:
 
- **Color by** system, temperature, pressure, flow rate or material class, with linear or log scales.
- **Operating and accident scenarios** for every design: normal operation, loss-of-coolant accidents, station blackout, and design-specific events such as the TMI-2 sequence, the EBR-II 1986 inherent-safety tests, the 1995 Monju sodium leak and an MSRE freeze-valve drain. Idle systems are greyed out, failed components are marked, and a narrative box lists the sequence of events.
- **Drill down** from a component to its parts (seals, studs, tubes, internals), with materials, degradation concerns and source links.
- **Filters** to hide SSC types or material classes.
- **SI / US units** throughout.
- **Editable data**: correct a value, add a part, or add a whole new reactor from a template, then export the dataset as JSON to share with a class.
## Reactors included
 
| Family | Designs |
|---|---|
| PWR | Westinghouse 4-loop (Vogtle 1/2 class), Westinghouse AP1000, Babcock & Wilcox 177-FA (TMI / Oconee class), Combustion Engineering System 80 (Palo Verde class), VVER-1000 (V-320), Framatome EPR, Shippingport (1957) |
| BWR | GE BWR/4 with Mark I containment, ABWR, ESBWR |
| PHWR | CANDU 6 |
| Integral PWR (SMR) | NuScale Power Module |
| Sodium-cooled | Pool-type SFR (PRISM class), TerraPower Natrium, EBR-II, Monju, Aalo Atomics Aalo-X |
| Lead-cooled | BREST-OD-300 |
| High-temperature gas | HTR-PM pebble bed |
| Molten salt | Molten Salt Reactor Experiment (MSRE) |
| Research | MIT Research Reactor (MITR-II), Idaho State University AGN-201M |
 
## Using it in class
 
- Start in **2D systems** with a single design and turn layers on one at a time.
- Switch **Color by** to temperature or pressure to show the physical state of each system, then pick a **Condition** to see what changes in an accident.
- Use **Side by side** to compare design choices, for example an active-safety PWR against the AP1000, or a loop-type against a pool-type sodium reactor.
- Use **Scale comparison** to make the size differences between a 5 W teaching reactor and a 4,590 MWt EPR concrete.
- Have students find and correct a value with **Edit data**, citing the source they used.
The **?** button in the header opens the built-in help.
 
## Data model
 
Each reactor is one JSON document, editable in the tool under **Edit data**:
 
| Field | Purpose |
|---|---|
| `systems` | Layers: id, name and color. |
| `components` | Each has a system, type, material and a `geom`. |
| `geom` | Shape and position. Kinds: `cyl`, `domecyl`, `box`, `pipe`, `torus`, `bulb`, `tap`, `person`. Coordinates are in meters, y up. |
| `props` | `T_C`, `P_MPa`, `flow_kgs` for the color overlays. |
| `dims`, `concerns` | Descriptive dimensions and degradation or design notes. |
| `children` | Drill-down parts. |
| `sources` | Reference links. |
| `scenarios` | System and component states, property overrides and a narrative sequence. |
 
Edits are stored in the browser's local storage. Use **Export all (JSON)** to save or share a dataset and **Import JSON…** to load one. When a new version of the tool is opened, unedited built-in reactors are refreshed and the previous saved dataset is kept as a backup in that browser.
 
## Sources
 
Values are drawn from NRC documents (Reactor Concepts Manual, technology training manuals, NUREGs, design control documents and safety evaluation reports), IAEA publications, national laboratory reports, vendor material, textbooks and published papers. Each reactor and many components carry their own source links in the detail panel.
 
## Limitations
 
- Drawings are schematic. One loop is usually drawn in 2D and replicated in 3D, and equipment is positioned for clarity rather than surveyed location.
- Scenario values are representative of each event, not the output of a transient calculation.
- Some designs rely on limited public information, and their dimensions are marked as representative.
- The tool is designed for desktop browsers; it runs on tablets and phones with reduced layout.
 
## License
 
MIT License. Copyright (c) 2026 Curtis Lee Smith. See `LICENSE`.
 
Reactor Dissection includes [three.js](https://threejs.org/) r128, which is also distributed under the MIT License.
 
