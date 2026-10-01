# Enterprise AI Marketing Operations Platform

An enterprise-style multi-agent AI marketing automation system built with n8n.

This project automates key marketing operations from campaign intake through AI-driven workflow processing, review, approval, campaign execution workflows, analytics, and centralized campaign data management.

## Overview

The Enterprise AI Marketing Operations Platform is designed as a multi-agent automation system for managing marketing campaign workflows.
It connects AI-powered decision-making with structured business workflows to reduce repetitive manual work and provide a centralized campaign tracking process.
The workflow starts with structured campaign intake and ends with campaign information being stored in Google Sheets.

## Problem

Marketing operations often involve multiple repetitive steps, including:
- Understanding campaign requirements
- Researching the target audience and competitors
- Creating campaign content
- Reviewing content against brand requirements
- Managing approvals
- Preparing platform-specific campaign workflows
- Tracking campaign progress
- Maintaining centralized campaign records

Handling these steps manually makes campaign operations difficult to track and coordinate.

## Solution

This project uses n8n to coordinate specialized AI-powered workflow components through a Marketing Manager agent that routes each campaign to the relevant specialist agents — 10 AI Agent nodes in total (1 manager + 9 specialists).
The system processes campaign information through dedicated stages and maintains structured campaign data throughout the workflow.
A human approval stage is also included where required before continuing the campaign workflow.

## Multi-Agent Architecture

The system is coordinated by a **Marketing Manager agent**, which routes each campaign to the relevant specialist agents — **10 AI Agent nodes in total** (1 manager + 9 specialists).

The functional operational areas include:

- **Marketing Manager** (orchestrates and routes to specialists)
- **Market Research**
- **Competitor Analysis**
- **Audience Research**
- **Content Writer**
- **Brand Review**
- **Human Approval**
- **LinkedIn Campaign**
- **Email Campaign**
- **Analytics**

Each specialized agent handles a defined part of the overall marketing workflow, and returns structured data consumed by downstream nodes. The architecture is designed to keep marketing operations modular rather than relying on a single AI prompt for the entire process. Specialist agents are invoked based on the Manager agent's routing decision for that campaign, not run as a fixed sequential chain every time.

## Workflow Flow

```text
Campaign Intake (Webhook)
      ↓
Campaign Information Processing
      ↓
Marketing Manager Agent (routes to relevant specialists)
      ↓
AI Marketing Specialist Agents
  ├─ Market Research
  ├─ Competitor Analysis
  ├─ Audience Research
  ├─ Content Writer
  ├─ Brand Review
  ├─ LinkedIn Campaign
  ├─ Email Campaign
  └─ Analytics
      ↓
Human Approval Stage
      ↓
Consolidated Campaign Data
      ↓
Google Sheets (Final Data Store)
```

## Campaign Intake

The workflow accepts structured campaign information via webhook:

- Company Name
- Contact Name
- Contact Email
- Campaign Type
- Business Goal
- Target Audience
- Primary Platforms
- Brand Voice
- Campaign Deadline

A unique campaign ID is generated for tracking in the format: `CMP-YYYYMMDD-HHmmss`

Operational tracking fields include:

- `status` (e.g., Pending)
- `priority` (e.g., Medium)
- `approval` (e.g., Yes)
- `progress` (e.g., 0)
- `created_at`
- `updated_at`

## Human Approval

Human approval is included as an explicit control point in the workflow. This ensures critical marketing outputs undergo human review before final logging or dispatch, avoiding unreviewed automated decisions.

## Final Data Store

Google Sheets serves as the final structured campaign data store, recording full campaign metadata, agent outputs, and execution timestamps in a centralized table.

## Technology Stack

- n8n (Workflow orchestration & node logic)
- Google Gemini (AI model for analysis, generation & structured review)
- Google Sheets (Centralized data store)
- Webhooks & APIs (Campaign intake & integration)
- JavaScript (Data transformation & formatting nodes)

## Key Features

- Multi-agent AI marketing workflow (10 AI Agent nodes: 1 manager + 9 specialists)
- Structured campaign intake via webhook
- Automated campaign ID generation
- Market research automation
- Competitor analysis automation
- Audience research processing
- AI-assisted content creation
- Brand review workflow
- Human approval stage
- LinkedIn campaign workflow
- Email campaign workflow
- Analytics workflow
- Centralized Google Sheets storage

## Example Campaign Input

```yaml
Company: ABC Corporation
Contact: John Smith
Campaign Type: Lead Generation
Target Audience: HR Managers & HR Directors in companies with 100-1000 employees
Primary Platforms: LinkedIn, Email
Brand Voice: Professional
Campaign Deadline: 2026-08-31
```

## Example Campaign Tracking

```yaml
Campaign ID: CMP-YYYYMMDD-HHmmss
Status: Pending
Priority: Medium
Approval: Yes
Progress: 0
```

## Evidence & Testing

This repository will contain verified evidence from the actual workflow:

- n8n full workflow overview
- Node configurations & execution evidence
- Campaign intake & AI output data
- Google Sheets final data store screenshots

All screenshots and examples are based on the actual portfolio project workflow.

## Project Scope

SEO automation is intentionally excluded from the scope of this project. The system focuses strictly on campaign intake, research, drafting, review, approval, platform workflows, and data logging.

## Data & Demo Notice

Any demonstration records or sample companies shown in screenshots or test data are strictly for demonstration purposes and clearly labeled as demo/sample data. No confidential business information or private customer data is stored in this repository.

## Security

API keys, credentials, OAuth tokens, and webhook secrets are strictly omitted. Any exported workflow JSON provided in this repository is thoroughly sanitized before upload.

## Limitations

This is an authentic portfolio project demonstrating multi-agent workflow architecture in n8n. It is not an enterprise-scale production deployment for an active company. AI executions are subject to model rate limits and quotas.

## Future Improvements

- Additional campaign distribution channels
- Automated multi-step email sequence triggers
- Enhanced reporting dashboards
- Webhook-based interactive approval buttons

These are future improvements and are not presented as currently implemented features.

## Project Status

Completed — Portfolio Project

## Author

**Faiziya Khan**

AI Automation Engineer | n8n | AI Agents | RAG | Workflow Automation

Email: khanfaiziya2@gmail.com
