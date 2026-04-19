# Data Access

The UNICEF MICS Round 6 datasets used in this project are not redistributed here.
They are subject to UNICEF's data access terms and are too large for GitHub.

---

## How to Access the Data

### Option 1: Use the Shared Google Drive (Recommended for Colab)

The project maintains a shared Google Drive folder with the required files (Viewer access, no sign-in required).
File IDs are already pre-filled in Section 0 of the notebook. Just open the notebook and run that cell.

If you need to update the file IDs manually (e.g., if the shared links expire), open the notebook's
**Section 0** and replace the values in `FILE_IDS`:

```python
FILE_IDS = {
    "Punjab": {
        "hl.sav": "YOUR_PUNJAB_HL_FILE_ID",
        "hh.sav": "YOUR_PUNJAB_HH_FILE_ID",
    },
    # ... etc
}
```

### Option 2: Download Directly from UNICEF

1. Visit the UNICEF MICS data portal: https://mics.unicef.org/surveys
2. Search for "Pakistan" and select the Round 6 surveys for each province:
   - Punjab 2017-18
   - Sindh 2018-19
   - Khyber Pakhtunkhwa 2019
   - Balochistan 2019-20
3. Register for a free account and request data access
4. Download the SPSS datasets for each province

### Option 3: World Bank Microdata Library

Some MICS datasets are also available via the World Bank Microdata Library:
https://microdata.worldbank.org

---

## Files Required per Province

The notebook uses exactly two files per province:

| File | Description |
|---|---|
| `hl.sav` | Household members roster. Primary file for all education and demographic variables. |
| `hh.sav` | Household questionnaire. Used only to extract HH15 (interview language, ethnicity proxy). |

---

## Expected Folder Structure (for local runs)

If running locally rather than on Colab, place files in this structure and set
`LOCAL_MODE = True` in Section 0 of the notebook:

```
Datasets/
├── Punjab/
│   ├── hl.sav
│   └── hh.sav
├── Sindh/
│   ├── hl.sav
│   └── hh.sav
├── KPK/
│   ├── hl.sav
│   └── hh.sav
└── Balochistan/
    ├── hl.sav
    └── hh.sav
```

Then update `LOCAL_BASE` in Section 0 to point to the parent `Datasets/` folder.

---

## Raw Data Summary

| Province | Survey Year | Raw Rows | Columns |
|---|---|---|---|
| Punjab | 2017-18 | 330,027 | 104 |
| Sindh | 2018-19 | 132,780 | 115 |
| KPK | 2019 | 178,631 | 99 |
| Balochistan | 2019-20 | 168,588 | 113 |
| **Merged** | -- | **810,026** | 121 |

Final analytical sample after preprocessing: **131,748** school-age children (ages 6-24).
