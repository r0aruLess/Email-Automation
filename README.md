 📬 Email Automation

A Python script that reads recruiter contacts from Google Sheets and automatically sends personalized GRC internship application emails via Gmail — with your resume attached.

---

## ✨ Features

- Reads company name, email, and notes directly from your Google Sheet
- Sends personalized emails for each contact using your own writing style
- Automatically attaches your resume to every email
- Creates a **"No. of Times Sent"** column in your sheet and updates it after every send
- Runs entirely on your local machine — no data leaves your computer except the emails themselves

---

## 🗂️ Folder Structure

```
resume-sender/
├── grc_email_sender.py   # Main script
├── credentials.json      # Google OAuth credentials (never share this)
├── token.pickle          # Auto-generated after first login (never share this)
└── resume.pdf            # Your resume
```

---

## ⚙️ Setup

### 1. Install Dependencies

```bash
python -m venv venv
venv\Scripts\activate        # Windows
source venv/bin/activate     # Mac/Linux

pip install google-auth google-auth-oauthlib google-auth-httplib2 google-api-python-client anthropic
```

### 2. Set Up Google Cloud

1. Go to [console.cloud.google.com](https://console.cloud.google.com)
2. Create a new project
3. Enable **Gmail API** and **Google Sheets API**
4. Go to **APIs & Services → OAuth Consent Screen**
   - Choose **External**
   - Add your Gmail as a test user
5. Go to **Credentials → Create Credentials → OAuth 2.0 Client ID**
   - Choose **Desktop App**
   - Download the JSON and rename it to `credentials.json`
   - Place it in the project folder

### 3. Set Up Your Google Sheet

Your sheet should have these columns:

| Organisation | Email | Linkedin | Sales Notes |
|---|---|---|---|
| Company XYZ | recruiter@xyz.com | linkedin.com/in/... | AI governance, risk audits |

### 4. Fill in the Config

Open `grc_email_sender.py` and fill in the `CONFIG` section at the top:

```python
GOOGLE_SHEET_ID = "your_sheet_id_here"   # From your Sheet URL
SHEET_TAB_NAME  = "Sheet1"
RESUME_PATH     = "resume.pdf"
YOUR_NAME       = "Your Full Name"
YOUR_EMAIL      = "you@gmail.com"
YOUR_PHONE      = "+91 XXXXXXXXXX"
YOUR_LINKEDIN   = "linkedin.com/in/yourprofile"
YOUR_BACKGROUND = "Brief description of your background..."
```

---

## 🚀 Running the Script

```bash
python grc_email_sender.py
```

On first run, a browser window will open asking you to authorize Gmail and Sheets access. After that, it runs automatically.

---

## 📧 Email Template

The script sends a natural, personalized email to each recruiter.

---

## 📊 Tracking

After each email is sent, the script automatically updates a **"No. of Times Sent"** column in your Google Sheet. This lets you track who has been contacted and how many times.

---

## 🔒 Security Notes

**Never share or commit these files:**
- `credentials.json`
- `token.pickle`

Add them to your `.gitignore`:

```
credentials.json
token.pickle
resume.pdf
```

If you accidentally expose them, immediately go to Google Cloud Console and delete/recreate your OAuth credentials.

---

## 🛠️ Troubleshooting

| Issue | Fix |
|---|---|
| `Found 0 contacts` | Check your sheet column names match exactly |
| `Access blocked` | Add your Gmail as a test user in OAuth consent screen |
| `Error 404 sheet not found` | Double check your `GOOGLE_SHEET_ID` in the config |
| `token.pickle` errors | Delete `token.pickle` and re-run to re-authenticate |
| Pylance import warnings in VS Code | Press `Ctrl+Shift+P` → "Python: Select Interpreter" → select `venv` |

---

## 📄 License

MIT — free to use and modify for personal use.sonal use.
