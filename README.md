# Email Routing Workflow – Integration Guide

This workflow can be reused in your own system.  
To adapt it, modify the following four parts.

---

## 1) Trigger – Connect Your Email System

The current workflow uses a webhook trigger.

Replace it with your own email source:

- Gmail / Outlook webhook
- Internal SMTP gateway
- Helpdesk email ingestion
- Any system that can send an HTTP request

Ensure the payload includes:

- `subject`
- `sender`
- `body`
- `message_id`

The trigger should only forward structured email data.  
Do not add routing logic here.

---

## 2) Code Node – Customize Email Cleaning

Update the cleaning logic to match your environment:

- Remove internal signatures
- Strip unsubscribe links
- Remove forwarded thread history
- Normalize email content

This node should only preprocess text.  
Do not add classification logic here.

---

## 3) Classifier – Define Your Own Categories

Replace the default categories with your internal routing model.

Example:

support
billing
security
sales
other


Keep the category set fixed.  
The model must select from predefined values only.

---

## 4) HTTP Node – Connect to Your System

Replace the existing HTTP integration with your own:

- Ticketing system API
- CRM API
- Slack / internal notifications
- Custom Dify plugin

This node is responsible for executing the routing decision.

---

## Suggested Development Timeline

- **Week 1**: Connect trigger + implement cleaning + define categories  
- **Week 2**: Integrate HTTP output + enable controlled routing  
- **Week 3**: Tune thresholds and monitor misroutes  

Most teams can deploy a stable version within 2–3 weeks.

---

## What You Do NOT Need to Change

- Overall workflow structure  
- Conditional routing branches  
- Verification logic  

Only adapt:

1. Trigger  
2. Cleaning  
3. Categories  
4. Output integration 
