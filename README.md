# CLASS·SELECT — RELION 2D Class Browser

A browser-based 2D class average browser and particle exporter for RELION classification workflows, supporting polymorph-aware curation across multiple classification rounds.

No installation required — open the HTML file in any modern browser.

---

## Overview

CLASS·SELECT replaces the binary accept/reject decision of RELION's standard class selection job with a richer workflow: classes are assigned to up to eight named, colour-coded groups, so that distinct structural populations (polymorphs, conformations, junk) can be tracked and exported separately, even across several rounds of 2D classification.

---

## Features

### Loading data
- **Model STAR** (`*_model.star`, required): provides class distributions and estimated resolutions
- **Particles STAR** (`run_it*_data.star`, recommended): enables accurate per-class particle counts and is required for a complete `particles.star` export with the optics table and all columns
- **MRC stack** (`*_classes.mrcs`, optional): displays the real class average images; without it, synthetic placeholder images are shown
- **Similarity matrix** (`.csv`, `.tsv`, or `.txt`, optional): enables "similar class" suggestions; supports multiple matrices per file, with a dropdown to switch between them
- A built-in **Load Demo** option populates the tool with synthetic data for trying it out without RELION files

### Class grid and inspection
- Grid display of all classes with adjustable zoom, search, sorting (by index, distribution, or estimated resolution), and filtering (all, unassigned, rejected, or a specific group)
- Per-class detail panel showing the class image, key metadata, and group assignment buttons
- Adjustable display contrast (σ-based) and LUT inversion
- A resolution bar overlay on each class card for at-a-glance quality assessment

### Group assignment
- Up to eight named, colour-coded groups plus a separate "Rejected" category
- Manual assignment by clicking a class while a group is active, with keyboard shortcuts for fast curation
- Automatic assignment to the active group based on configurable distribution and resolution thresholds
- Session statistics (classes loaded, assigned, rejected, particles kept) displayed live in the sidebar

### Similarity-based assistance
- Load one or more similarity matrices to highlight related classes directly in the grid
- Adjustable similarity threshold slider with live grid highlighting
- Similar-class suggestions are shown in the detail panel for the currently inspected class

### Export
- Export selected groups as a filtered `particles.star`, preserving all original metadata columns when a `*_data.star` file was loaded
- Export modal lets you choose which groups to include and set the output filename

---

## Installation

No installation is required.

Download or clone the repository and open the HTML file in a modern browser (Chrome, Firefox, or Edge recommended):

```
git clone <repository-url>
cd <repository-folder>
open relion_class_selector.html
```

Alternatively, double-click the HTML file to open it directly.

---

## File Format Requirements

### Model STAR (`*_model.star`)
Must include `_rlnClassDistribution`, `_rlnEstimatedResolution`, and `_rlnReferenceImage`.

### Particles STAR (`*_data.star`)
Must include `_rlnClassNumber`. Used for accurate particle counts and for generating a complete export.

### Similarity Matrix
A square N×N matrix in CSV, TSV, or plain-text format. Values are automatically normalized to [0,1] if they fall outside that range. Optional row/column class labels are supported, and a single file may contain multiple matrices separated by blank lines or `# name` headers.

---

## Limitations

- Runs entirely client-side; very large `.mrcs` files may impact browser performance
- No persistence beyond the session — state is lost on reload unless exported
- Export of a complete `particles.star` requires a valid `*_data.star` file; without it, particle counts are estimates only and export will be incomplete

---

## License

GNU General Public License v3.0 (GPLv3). See the `LICENSE` file in this repository for the full license text.

---

## Contact

For questions or feedback, please open an issue in the repository.
