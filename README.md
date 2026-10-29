# AI Lead Scorer (n8n + Claude)

A website form that scores every inquiry from 1 to 10 with Claude, logs it in Google Sheets, and sends a Gmail alert when the score is 7 or higher, with a draft reply.

**See the case study:** open `index.html` or this repository's GitHub Pages site.

## How to use it
1. In n8n: **Import from File** → `ai-lead-scorer-n8n.json`.
2. *Claude scores the lead* node: create a **Header Auth** credential named `x-api-key` with your Anthropic API key.
3. *Save to Google Sheets* node: connect your account and paste the URL of a sheet with a tab called `Leads` and these columns in row 1:
   `date, name, email, company, budget, message, score, category, reason, suggested_reply`
4. *Notify me via Gmail* node: connect your account and replace `YOUR_EMAIL@gmail.com`.
5. Click **Execute workflow** and submit the form.

The JSON contains no API keys or personal data.
