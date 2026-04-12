# 📝 Fill Records V2 - Field-by-Field Method

**Created:** 2026-04-12  
**Version:** 2.0  
**Status:** ✅ Enhanced!

---

## 🎯 Better Approach: Targeted Replacements

Instead of replacing all occurrences, replace specific text patterns.

---

## 📋 Field Mapping by Form

### F/08 - Order Form
| Field | Template | Replace With |
|-------|----------|-------------|
| Serial | {{SERIAL}} | F/08-007 |
| Date | {{DATE}} | 12/04/2026 |
| Customer | Customer Name | BatFast |
| Mode | Mode Of Receipt | Email |
| Product | Product Name | BatFast AI Annotation |
| Specifications | ... | 6000 image annotation |
| Qty | ... | 6000 |
| Test Certificate | ... | Yes |
| Delivery | ... | 20 days |

---

### F/11 - Production Plan  
| Field | Template | Replace With |
|-------|----------|-------------|
| Serial | {{SERIAL}} | F/11-007 |
| Date | {{DATE}} | 12/04/2026 |
| Month | Month | April 2026 |
| Product 1 | Product | BatFast |
| Batch No 1 | Batch No | BF-001 |
| Plan For 1 | Plan For Completion | 6000 tasks |
| Actual 1 | Actual Completion % | 100% |

---

### F/19 - Product Description
| Field | Template | Replace With |
|-------|----------|-------------|
| Serial | {{SERIAL}} | F/19-007 |
| Product Name | Product Name | BatFast AI Annotation |
| Process | Process name | AI Data Annotation |
| Composition | Composition | Annotation Team, TL, QA |
| End Product | End Product | Annotated images/videos |
| Storage | Storage Condition | Client platform |

---

### F/50 - Customer Property
| Field | Template | Replace With |
|-------|----------|-------------|
| Serial | {{SERIAL}} | F/50-007 |
| Date | Date | 12/04/2026 |
| Property Name | Name Of Property | BatFast Data |
| Purpose | Purpose | AI Training |
| Qty | Received Qty | 6000 |
| Customer | Customer Name | BatFast |

---

## 🛠 Implementation V2

```bash
# Download template
curl -sL "https://drive.google.com/uc?export=download&id=TEMPLATE_ID" -o template.docx

# Extract
unzip -oq template.docx -d work/

# Make targeted replacements using unique context
cd work/
sed -i 's/{{SERIAL}}/F\/11-007/g' word/document.xml
sed -i 's/{{DATE}}/12\/04\/2026/g' word/document.xml
sed -i 's/{{CUSTOMER}}/BatFast/g' word/document.xml

# Can also add new lines for table rows
echo "<w:p><w:r><w:t>New Data</w:t></w:r></w:p>" >> word/document.xml

# Repackage
zip -rq filled.docx .

# Upload
gog drive upload filled.docx --account ACCOUNT --parent FOLDER_ID
```

---

## ⚠️ Limitations

- Need unique markers for each field
- Table structure in XML is complex
- Some fields need new XML elements

---

**Tested:** 2026-04-12  
**Status:** V2 documented

*Last updated: 2026-04-12*
