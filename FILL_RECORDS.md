# 📝 Fill Records Programmatically - Method G

**Created:** 2026-04-12  
**Version:** 1.0  
**Status:** ✅ Working!

---

## 🎯 Problem

Need to fill QMS docx templates with data programmatically

---

## ✅ Solution: Method G

### Steps:

1. **Download** template docx
2. **Unzip** to extract XML
3. **Sed** to replace text values in XML
4. **Zip** back to docx
5. **Upload** to Drive

---

## 🛠 Implementation

```bash
# 1. Download template
curl -sL "https://drive.google.com/uc?export=download&id=TEMPLATE_ID" -o template.docx

# 2. Extract
unzip -oq template.docx -d extracted/

# 3. Replace values (sed)
cd extracted/
sed -i 's/OLD_VALUE/NEW_VALUE/g' word/document.xml
# Repeat for each field...

# 4. Repackage
zip -rq filled_record.docx .

# 5. Upload
gog drive upload filled_record.docx --account ACCOUNT --parent FOLDER_ID
```

---

## 📋 Field Mapping (F/11 Example)

| Field | Replace From | Replace To |
|-------|--------------|------------|
| Product Name | Video Detection Project | BatFast - AI Annotation Project |
| Process | Video Classification | AI Data Annotation |
| Composition | Agent Team | Annotation Team |
| End Product | Labeled videos | Annotated images/videos |
| Storage | Client platform | Client platform |
| Distribution | Client platform | Client platform |

---

## ⚠️ Limitations

- Sed replaces ALL occurrences of text
- For multiple records, need unique markers or field-specific IDs
- Works best for single-record fills

---

## 🔧 Future Improvements

- Field-by-field replacement using XML IDs
- JSON data to auto-fill multiple fields
- Variable placeholders in template

---

**Tested:** 2026-04-12  
**Result:** Successfully filled F/11 record!

*Last updated: 2026-04-12*
