# 📧 Email Reporter Skill

**Created:** 2026-04-11  
**Skill:** Send daily automated reports via email

---

## 🎯 What I Do

Every day at 9:00 AM UTC (or when triggered), I:
1. Scan Drive folders for changes
2. Check active projects status
3. Generate summary report
4. Email to your-email@example.com

---

## 📊 Report Contents

### Daily Status Email

```
Subject: KEPV18 Daily Report - [DATE]

📊 Active Projects: [count]
- Project 1: Status
- Project 2: Status
...

📁 New Files: [count]
- File name

⚠️ Action Needed: [if any]

---
KEPV18 QMS System
```

---

## ⏰ Schedule

- **Daily:** 9:00 AM UTC
- **Trigger:** "send report" or "daily report"

---

## 📧 Email Settings

- **To:** your-email@example.com
- **From:** your-email@example.com (via gog)
- **Format:** Markdown + plain text

---

## 🔧 Implementation

Using `gog gmail send`:
```bash
gog gmail send --account your-email@example.com \
  --to your-email@example.com \
  --subject "KEPV18 Daily Report - $(date +%Y-%m-%d)" \
  --body "report content"
```

---

**Status:** Ready to use! 🔥

*Last updated: 2026-04-11*
