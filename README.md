# AI Lead Scorer Pro (n8n + Claude)

A website form that scores every inquiry from 1 to 10 with Claude, filters out spam and duplicates, logs every lead in Google Sheets, and, when a lead is hot, sends you a Gmail alert and leaves a reply draft ready in your Gmail Drafts.

**See the case study:** https://fernando7885.github.io/calificador-leads/

**Get AI Lead Scorer Pro (template + sheet templates + setup guide):** https://fernandovibes8251.gumroad.com/l/ai-lead-scorer-n8n

## How it works
1. A built-in n8n form collects name, email, company, budget and message.
2. The workflow reads your **Settings** tab and your recent leads from Google Sheets.
3. Spam and duplicates are caught before they reach Claude and logged in a **Filtered** tab.
4. Claude scores each valid lead (1-10), labels it hot / warm / cold, explains why and writes a reply in the contact's language.
5. Every scored lead is logged in the **Leads** tab.
6. Hot leads (score at or above your threshold) trigger a Gmail alert, and a reply draft addressed to the lead is created in Gmail Drafts.

## What's new in Pro (compared with the original version)

| | Original | Pro |
|---|---|---|
| Configuration | Edit the prompt and threshold inside the workflow | Everything in a **Settings** tab in Google Sheets, no need to open the workflow |
| Business context | Generic prompt | Claude uses your business name, what you sell, your ideal client and who is not a fit |
| Hot threshold | Fixed at 7 | Set your own (`hot_threshold`) |
| Spam filter | None | Blocked words, blocked email domains (disposable inboxes), messages with 3+ links, links in the name field |
| Duplicates | None | Same email within a configurable window (`duplicate_window_days`, default 30) is skipped |
| Filtered leads | n/a | Logged to a **Filtered** tab with the reason, and never sent to Claude (saves API cost) |
| Reply | Suggested reply inside the alert email | Also saved as a **Gmail draft** to the lead, ready to review and send |
| Reply style | Fixed | Your own tone (`reply_tone`) and signature (`reply_signature`) |
| Sheet setup | Create the columns by hand | Ready-made CSV templates for the Leads, Filtered and Settings tabs |
| Error handling | n/a | If Claude does not return valid JSON, the lead is still logged with category `review` |

## Settings tab

| setting | example |
|---|---|
| `business_name` | Your Business Name |
| `what_you_sell` | Web design for local restaurants |
| `ideal_client` | Clear need, budget over USD 2,000, wants to start within 3 months |
| `not_a_fit` | Students, job seekers, vendors pitching their services |
| `hot_threshold` | 7 |
| `reply_tone` | Friendly, concise, ends by proposing a short call |
| `reply_signature` | Your Name |
| `blocked_words` | seo services, backlinks, guest post, crypto, casino, loan offer |
| `blocked_domains` | mailinator.com, yopmail.com, tempmail.com, 10minutemail.com, guerrillamail.com |
| `duplicate_window_days` | 30 |

## What's in the Gumroad package
- `ai-lead-scorer-pro-n8n.json`: the n8n workflow, with no credentials or personal data.
- `sheet-templates/`: `Leads.csv`, `Filtered.csv` and `Settings.csv`, to import as the three tabs of your Google Sheet.
- `Setup-Guide.pdf`: step-by-step setup in English and Spanish.

## Requirements
- n8n (n8n Cloud or self-hosted).
- An Anthropic API key (the workflow uses Claude Haiku; usually under 1 cent per lead, depending on usage).
- A Google account for Google Sheets and Gmail.

Importing takes a couple of clicks; connecting your credentials and filling in the Settings tab takes about 15 minutes.

## Changelog
- **Pro:** Settings tab, spam and duplicate filtering with a Filtered tab, business-aware prompt, custom threshold, reply tone and signature, Gmail reply drafts, sheet templates, fallback for invalid AI output.
- **v1:** form, Claude scoring, Google Sheets log and Gmail alert for leads scoring 7 or higher.

Built with n8n, the Anthropic API (Claude Haiku), Google Sheets and Gmail.
