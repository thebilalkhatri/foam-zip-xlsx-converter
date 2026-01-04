# FOAM ZIP ⇄ XLSX Converter

A browser-based utility to convert **FOAM / Camunda form ZIP files** into an editable Excel (`.xlsx`) format and safely merge updates back into the original ZIP — without breaking form structure or identifiers.

This tool is especially useful for **business analysts, QA teams, and developers** who need to bulk-edit form component properties outside of JSON.

---

## 🚀 Features

- 📦 Convert `.form` / `.json` files inside a ZIP → Excel
- 📊 One Excel row per component `properties` object
- 🔁 Safe round-trip editing (ZIP → XLSX → ZIP)
- 🔒 **`form_id` is read-only**
  - Extracted from top-level form `id`
  - Never written back or injected into component properties
- 🧠 Preserves original:
  - File paths
  - JSON hierarchy
  - Component structure
- ✂ Automatically truncates very long values (Excel-safe)
- 🌐 100% client-side (no backend, no uploads)

---

## 🧩 Excel Columns Explained

| Column Name | Description |
|------------|------------|
| `form_id` | Top-level unique Form ID (read-only) |
| Other columns | Component-level properties |
| `_FILE_PATH` | Original file path inside ZIP |
| `_JSON_PATH` | Exact JSON pointer to the properties object |
| `_ROW_ID` | Internal row identifier (do not edit) |

> ⚠️ **Do not rename or delete** `_FILE_PATH` or `_JSON_PATH`.  
> These are required to map Excel rows back to JSON correctly.

---

## 🔐 Safety & Design Guarantees

- ❌ `form_id` edits in Excel are ignored intentionally
- ❌ `form_id` is never written into `properties`
- ❌ No data is uploaded to any server
- ✔ Original ZIP structure remains intact
- ✔ Only component `properties` are updated

---

## 🛠 Tech Stack

- **HTML5**
- **Vanilla JavaScript**
- **JSZip**
- **SheetJS (xlsx)**

No frameworks. No build step. Runs entirely in the browser.

---

## ▶ How to Use

### 1️⃣ Export ZIP → Excel
1. Open the app
2. Select a FOAM ZIP file
3. Click **Convert ZIP → XLSX**
4. Edit the generated Excel file

### 2️⃣ Import Excel → Updated ZIP
1. Select the edited Excel file
2. Select the original ZIP file
3. Click **Convert → Updated ZIP**
4. Download the updated ZIP

---

## 🌍 Live Demo (GitHub Pages)

Once GitHub Pages is enabled, the app will be available at:

https://thebilalkhatri.github.io/foam-zip-xlsx-converter/

---

## 📂 Recommended Repository Structure

foam-zip-xlsx-converter/
│
├── index.html
├── README.md
├── LICENSE
├── jszip.min.js
└── xlsx.full.min.js

---

## ⚠ Notes & Limitations

- Designed for FOAM / Camunda-style form schemas
- Large text values are truncated for Excel safety
- Only `.form` and `.json` files are processed
- Nested `properties` objects are fully supported

---

## 📄 License

MIT License

You are free to use, modify, and distribute this project.
