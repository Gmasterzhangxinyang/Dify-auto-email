A Simple Roadmap to Ship Intent-Based Email Routing with Dify
If you want this to land successfully, don’t start with “AI reads email.” Start with a small, controlled workflow you can extend.
1. Import the DSL, then swap the trigger
Use our DSL as the backbone (clean → classify → route → output).
 The trigger is pluggable: keep your existing email system and just push emails into Dify.
- Gmail / Outlook / IMAP → webhook to Dify
- Internal email gateway → HTTP trigger
- Any system that can send JSON → works
2. Replace the “business logic” with your own routing rules
Keep the workflow structure, but customize three things:
- Categories (your real teams): tech support / billing / security / sales / other
- Hard boundaries: which categories must be reviewed (e.g., security)
- Confidence thresholds: when to auto-route vs. send to review
AI proposes intent. Workflow decides.
3. Output to your tools via HTTP or a plugin
Don’t rebuild your ticketing/CRM. Just send routing results downstream.
- HTTP webhook to your ticketing system / Slack / CRM
- Or build a Dify plugin if you need auth + deeper integration
4. Recommended timeline
- Week 1: Connect trigger + run in “observe only” mode (log + measure)
- Weeks 2–3: Turn on auto-routing for safe categories, keep review for sensitive/low-confidence
- Weeks 4–6: Integrate with internal systems (HTTP/plugin) + expand categories and coverage
That’s it. Start small, keep boundaries hard-coded, scale once routing is stable.
