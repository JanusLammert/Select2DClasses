# RELION 2D Class Selector

A browser-based tool for interactive inspection, curation, and export of 2D class averages from RELION classification workflows.

---

## Overview

The **RELION 2D Class Selector** is a standalone HTML application designed to streamline the manual selection and grouping of 2D classes. It provides a structured interface for evaluating class quality, organizing classes into user-defined groups, and exporting curated particle subsets.

The application runs entirely in the browser and requires no installation or external dependencies.

---

## Features

### Class Visualization
- Grid-based display of all 2D classes
- Adjustable zoom and contrast
- Search, sorting, and filtering capabilities
- Detailed per-class inspection panel

### Class Assignment and Curation
- Assignment of classes to up to 8 user-defined groups
- Rejection of low-quality classes
- Keyboard shortcuts for efficient workflows
- Automated assignment based on distribution and resolution thresholds

### Data Integration
Supports standard RELION output files:
- `*_model.star` (required)
- `run_it*_data.star` (recommended)
- `*_classes.mrcs` (optional)
- Similarity matrices (`.csv`, `.tsv`, `.txt`, optional)

### Similarity-Based Assistance
- Load one or multiple similarity matrices
- Highlight related classes in the grid
- Display similarity-based suggestions in the detail panel

### Export Functionality
- Export selected classes as a filtered `particles.star`
- Preserves metadata when a `*_data.star` file is provided

---

## Installation

No installation is required.

Download or clone the repository and open the HTML file in a modern web browser (Chrome, Firefox, or Edge recommended).

```bash
git clone <repository-url>
cd <repository-folder>
open relion_class_selector.html
```

Alternatively, double-click the HTML file to open it directly.

---

## Usage

### 1. Load Input Files

Upon opening the application, the welcome screen allows loading of the following files:

#### Required
- **Model STAR (`*_model.star`)**  
  Provides class distributions and estimated resolutions.

#### Recommended
- **Particles STAR (`run_it*_data.star`)**  
  Enables accurate particle counts and full export functionality.

#### Optional
- **MRC Stack (`*_classes.mrcs`)**  
  Displays actual class images. If omitted, synthetic placeholders are used.

- **Similarity Matrix (`.csv`, `.tsv`, `.txt`)**  
  Enables similarity-based class suggestions.

Files can be added via drag-and-drop or file browser.

---

### 2. Explore and Inspect Classes

After loading:
- Classes are displayed in a grid layout
- Clicking a class opens the detail panel
- Sidebar controls allow:
  - Sorting by distribution or resolution
  - Filtering by assignment state or group
  - Adjusting display parameters

---

### 3. Assign Classes

#### Manual Assignment
- Select an active group in the sidebar
- Click on a class to assign it

#### Rejection
- Assign a class to the "Rejected" category

#### Automatic Assignment
- Configure thresholds:
  - Minimum class distribution (%)
  - Maximum resolution (Å)
- Execute auto-assignment to the active group

---

### 4. Similarity Matrix Integration (Optional)

If a similarity matrix is loaded:
- Select the active matrix from the dropdown menu
- Adjust the similarity threshold
- Enable or disable grid highlighting
- Inspect suggested similar classes in the detail panel

Supported formats:
- CSV, TSV, or TXT
- Optional headers
- Multiple matrices per file (separated by blank lines)

---

### 5. Export Results

Use the **Export particles.star** function to generate a filtered output file.

- Select groups to include in the export
- Download the resulting `particles.star`

**Note:**  
If no `*_data.star` file is loaded, the export will be incomplete.

---

## File Format Requirements

### Model STAR (`*_model.star`)
Must include:
- `_rlnClassDistribution`
- `_rlnEstimatedResolution`
- `_rlnReferenceImage`

### Particles STAR (`*_data.star`)
Must include:
- `_rlnClassNumber`

Used for:
- Accurate particle counts
- Export generation

### Similarity Matrix
- Square matrix (N × N)
- Values normalized to [0,1] (automatic normalization applied if necessary)
- Optional class labels supported

---

## Limitations

- Entirely client-side; large `.mrcs` files may impact performance
- No persistence; session state is lost on reload
- Export functionality depends on availability of a valid `*_data.star`

---

## Recommendations

- Use similarity matrices to accelerate class grouping
- Begin with automated assignment and refine manually
- Use filtering (e.g., unassigned classes) to streamline curation
- Rename groups to reflect structural or quality categories

---

## License

Specify license information here.

---

## Contributing

Contributions, suggestions, and improvements are welcome. Please open an issue or submit a pull request.

---

## Contact

For questions or feedback, please open an issue in the repository.
