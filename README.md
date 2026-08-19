# Anesthesia Preference Card Builder

**Author:** Tony Kim, MD — Baylor College of Medicine, Department of Anesthesiology  
**Version:** Current  
**File:** `AnesthesiaPreferenceCardBuilder.html`

---

## Overview

The Anesthesia Preference Card Builder is a self-contained, mobile-optimized web application for creating structured anesthesia preference cards. It is designed for use by anesthesiologists and CRNAs at BCM-affiliated institutions to document surgeon- and procedure-specific anesthesia preferences in a standardized, shareable format.

The entire application lives in a **single HTML file** — no installation, no server, no internet connection required after the initial load of the SheetJS library.

---

## Getting Started

1. Download `AnesthesiaPreferenceCardBuilder.html`
2. Open it in any modern web browser (Safari, Chrome, Firefox, Edge)
3. Works on **iPhone, Android, iPad, and desktop**
4. No login or account required

---

## Features

### 📱 Mobile-First Design
- Optimized for phone use with large touch targets (38–44px minimum)
- Sticky header and tab navigation always visible while scrolling
- 15px input font size prevents iOS auto-zoom on focus
- Full-screen layout on mobile; card layout with shadow on desktop

### 🌙 Light / Dark Mode
- Toggle between light and dark themes with the 🌙/☀️ button in the header
- Theme preference is saved automatically and persists between sessions

### 📊 Progress Tracker
- A progress bar in the header fills as key fields are completed
- Tracks: surgeon name, procedure, institution, technique, position, airway, induction, and maintenance

### 🔍 CPT Code Lookup
- Enter a 5-digit CPT code to auto-fill the procedure name
- Type a procedure name to see matching CPT codes in a dropdown
- Covers ~150 common OR procedures across all surgical specialties
- Procedure field remains manually editable if the code is not found

---

## Tab Structure

The form is organized into five tabs:

| Tab | Contents |
|-----|----------|
| **Basic Info** | Surgeon/Proceduralist name, Procedure, CPT code, Case type, Date created, Institution, Anesthesia technique, Positioning |
| **Airway & Access** | Airway device, Tape preference, ET/LMA size, Extubation plan, PIV gauge/sites/notes, Arterial line & central access |
| **Medications** | Premedications, Induction agents & approach, Maintenance agents, TIVA infusions, Fluid/hemodynamic considerations, PONV prophylaxis |
| **Regional & Intraop** | Regional blocks/neuraxial, Intraoperative medications (categorized), NMB reversal |
| **Equipment & Notes** | Equipment & monitoring (categorized), Key anesthetic concerns, General notes, Submitted by, Export & email |

---

## Selection Options Reference

### Institutions
Ben Taub · BSLMC · TCH · VA · Vintage

### Anesthesia Techniques
Bier Block · Epidural · General · MAC · Regional · Spinal · TIVA

### Positioning
Supine · Lateral (L/R) · Prone · Lithotomy · Trendelenburg · Reverse Trendelenburg · Beach chair · Park bench · Sitting · Bed 90° · Bed 180° · Prone-jackknife · Thoracoabdominal

### Airway Devices
Oral ETT · Nasal ETT · Nasal RAE · ETT MLT · Wire reinforced ETT · Wire reinforced ETT – Dragonfly · NIMs tube · LMA Classic/Supreme · LMA with gastric port · Bronchial blocker · Jet ventilation · Awake FOB intubation · DLT (left/right) · Tracheostomy tube · Natural airway / MAC

### Tape Preference
ETT taped left · ETT straight back · ETT with accordion

### Intraoperative Medications (by category)

| Category | Medications |
|----------|-------------|
| Antibiotics | Cefazolin 2g IV, Cefazolin 3g IV (>80 kg), Vancomycin 15 mg/kg IV |
| Anticoagulation | Heparin 5,000u SQ (DVT), Systemic heparin, Protamine |
| Vasopressors | Phenylephrine PRN, Ephedrine PRN, Norepinephrine infusion, Vasopressin 20u, Papaverine infusion |
| Antihypertensives | Esmolol bolus/infusion, Labetalol, Metoprolol, Nicardipine infusion |
| Diuretics | Furosemide 20mg IV, Mannitol 0.5 g/kg, Mannitol 1 g/kg |
| Analgesics | Ketorolac 30mg IV, Acetaminophen 1000mg IV, Magnesium 2g IV |
| Miscellaneous | Dexamethasone 8mg IV, Insulin (per glucose), TXA 1000mg IV, TXA infusion |

### Equipment & Monitoring (by category)

| Category | Items |
|----------|-------|
| Vascular & Hemodynamic | Arterial line kit, CVL kit, PA catheter, TEE probe |
| Neurological Monitoring | BIS monitor, NMT/TOF monitor, Neuromonitoring |
| Temperature & Warming | Temperature probe (esophageal), Bair Hugger upper/lower body |
| Airway Equipment | Fiberoptic bronchoscope, GlideScope / video laryngoscope |
| Resuscitation | Cell saver, Level 1 rapid infuser, Belmont infuser |
| Tubes & Drains | Foley catheter, OG tube, NG tube |
| Positioning & Protection | SCDs + compression stockings, Axillary roll, Shoulder rolls, Tegaderm on eyes, Eye tape / goggles, Prone view pillow, Foam prone pillow, Padded arm boards |

---

## Export Options

### ⬇ Export to Excel
Exports the completed card as a single structured row in an `.xlsx` file. Column headers are consistent across all exports, making it easy to paste rows into a master preference card spreadsheet.

**File naming convention:** `LastName_Procedure_YYYY-MM-DD.xlsx`

### 🖨 Print / Save PDF
Opens a formatted preference card in a new browser window. Use your browser's **File → Print → Save as PDF** to save. The printed card uses a two-column layout with BCM navy section headers and alternating row shading.

### 👁 Preview Card
Opens an inline preview modal of the formatted print card before printing.

### ✉ Send Excel & PDF by Email
Clicking **Send** triggers a three-step sequence:
1. Downloads the **Excel file** to your device
2. Opens a **PDF print window** — save it as PDF using your browser's print dialog
3. Opens your **email client** pre-addressed to `tony.kim@bcm.edu` with the full card summary in the body

Attach **both** the Excel and PDF files to the email before sending. All submissions will be reviewed.

---

## Master Spreadsheet Workflow

Each Excel export produces one data row with consistent column headers. To maintain a library of preference cards:

1. Export a completed card — an `.xlsx` file downloads automatically
2. Open the downloaded file (it contains one header row + one data row)
3. Open your master spreadsheet
4. Copy **row 2** (the data row) and paste it as a new row at the bottom of the master sheet
5. Repeat for each new card

The master sheet can then be filtered by surgeon, sorted by procedure, or searched by any field.

---

## Customization

All selectable options are defined as JavaScript arrays and objects near the top of the `<script>` section. To add or modify options:

- **Pill lists** (multi-select): find the relevant key in the `D` object (e.g. `D.premeds`, `D.blocks`) and add/remove items from the array
- **Categorized sections** (Intraop Medications, Equipment): find `INTRAOP_CATS` or `EQUIP_CATS` and add items to the appropriate category's `items` array
- **CPT codes**: add entries to the `CPT` object using the format `'XXXXX': 'Procedure description'`
- **Institutions**: edit the `D.institution` array
- **Default email**: change the `value="tony.kim@bcm.edu"` attribute on the `recipientEmail` input

---

## Technical Details

| Property | Detail |
|----------|--------|
| File type | Single self-contained HTML file |
| Dependencies | SheetJS (xlsx.js) via CDN — required for Excel export |
| Frameworks | Vanilla JavaScript, HTML5, CSS3 — no build step required |
| Browser support | Chrome, Safari, Firefox, Edge (modern versions) |
| Mobile support | iOS Safari, Chrome for Android, iPad |
| Theme persistence | Saved to `localStorage` as `apc-theme` |
| Offline use | Fully functional offline once CDN script is cached |
| Print engine | Native browser print dialog (`window.print()`) |
| Excel engine | SheetJS (XLSX.utils) |

---

## Institutions Supported

- **Ben Taub** — Harris Health System
- **BSLMC** — Baylor St. Luke's Medical Center
- **TCH** — Texas Children's Hospital
- **VA** — Michael E. DeBakey VA Medical Center
- **Vintage** — Baylor St. Luke's Medical Center at Vintage

---

## Notes & Limitations

- **CPT lookup** covers ~150 common surgical CPT codes. Codes not in the local table will show a "not found" notice — the procedure field can always be filled manually.
- **Email attachments** cannot be added programmatically via `mailto:` links. The Excel and PDF files must be manually attached before sending.
- **No data is stored or transmitted** by this application. All data exists only in the browser session and is cleared on page refresh or when "Clear all fields" is used.
- **All submissions will be reviewed** — the submitter's name is captured on the final tab and included in all exports.

---

*Baylor College of Medicine · Department of Anesthesiology · Tony Kim, MD*
