# 📝 Fill Records V3 - Complete Technical Guide

**Created:** 2026-04-12  
**Version:** 3.0  
**Status:** Documented - Needs Python library for precise fills

---

## 🎯 Current State

### ✅ Working Methods
1. **Copy Template** - Simplest, just copy and fill manually
2. **Copy Existing Record** - Copy filled record and modify (limited)

### ⚠️ Partial Working
- **Sed replacement** - Replaces ALL text matches, not specific fields

### ❌ Complex
- Direct XML modification - Table structures very complex

---

## 📊 Why It's Complex

The F/11 Production Plan table has complex XML like:
- `<w:tc>` (table cells)
- `<w:gridSpan w:val="2">` (spanning columns)
- Each row has ~10 columns with unique IDs
- Numbers like "1", "2", "3" appear multiple times in different contexts
- Headers vs Data rows are mixed in XML

---

## 🔧 What Needs Development

1. **Python with lxml** - Parse XML properly, find specific elements
2. **Create blank template** with {{PLACEHOLDERS}} for each field
3. **Smart replacement** - Replace only in specific locations

---

## 🎯 Recommended Approach

### Next Steps:
1. Create template with unique placeholder markers like:
   - `{{PRODUCT_NAME}}` instead of `Product Name`
   - `{{QTY}}` instead of `2026`
   
2. Then use targeted sed:
   ```bash
   sed -i 's/{{PRODUCT_NAME}}/BatFast/g' word/document.xml
   ```

3. OR use Python docx-template library

---

## 📋 Field Positions (From Analysis)

### F/11 Table Structure (Row 1 Example):
| Col | Field | What appears as |
|-----|-------|-----------------|
| 1 | Sr No | "1" |
| 2 | Product | "Video Detection" |
| 3 | Batch No | "VD-Batch115" |
| 4 | Plan Date | "28/02/2026" |
| 5 | Plan For | "400K-430K videos per day" |
| 6 | Actual Date | "27/02/2026" |
| 7 | Remarks | "Average achieved daily output" |
| 8 | Yield | "100%" |

---

## 🛠 Immediate Use

For now: **Copy existing record → Fill manually** is fastest.

To automate fully: Install Python with docx-template:
```bash
pip install docxtpl
```

Then use:
```python
from docxtpl import DocTemplate

doc = DocTemplate("template.docx")
doc.render({"product_name": "BatFast", "qty": 6000})
doc.save("filled.docx")
```

---

**Status:** Full automation needs more development

*Last updated: 2026-04-12*
