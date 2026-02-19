Email Routing Workflow – Integration Guide

This workflow can be reused in your own system.
You only need to replace four parts.

1. Trigger – Connect Your Email System

Current: Webhook trigger.

You should:

Connect Gmail / Outlook / internal mail gateway

Push email payload to the Dify webhook

Include subject, sender, body, message_id

No routing logic here. Just forward email data.

2. Code Node – Customize Cleaning

Current: basic email cleaning.

You should:

Remove your company’s signatures

Strip system footers / unsubscribe blocks

Normalize thread history

This node should only clean text.
No classification logic.

3. Classifier – Define Your Own Categories

Replace the default categories with your own:

Example:

support

billing

security

sales

other

Keep the category set fixed.
The model must choose from these only.

4. HTTP Node – Connect to Your System

Current: calls Front API.

You should replace this with:

Your ticketing system API

Your CRM

Slack / internal tool

Or a custom Dify plugin

This is where routing actually happens.

Suggested Timeline

Week 1: connect trigger + cleaning + categories

Week 2: integrate HTTP + enable routing

Week 3: tune thresholds + monitor misroutes

Most teams can ship a stable version in 2–3 weeks.

What Stays the Same

You do not need to change:

Overall workflow structure

Verification logic

Conditional routing branches

Just adapt trigger, cleaning, categories, and output.
