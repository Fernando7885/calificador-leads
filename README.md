# AI Lead Scorer (n8n + Claude)

A website form that scores every inquiry from 1 to 10 with Claude, logs it in Google Sheets, and sends a Gmail alert when the score is 7 or higher, with a draft reply.

**See the case study:** https://fernando7885.github.io/calificador-leads/

**Get the ready-to-import template + step-by-step setup guide:** https://fernandovibes8251.gumroad.com/l/tpsnjg

## How it works
1. A built-in n8n form collects name, email, company, budget and message.
2. Claude scores the lead (1-10), labels it hot / warm / cold, explains why and drafts a reply.
3. Every lead is logged in Google Sheets.
4. Hot leads (score 7+) trigger a Gmail alert.

Built with n8n, the Anthropic API (Claude Haiku), Google Sheets and Gmail.
