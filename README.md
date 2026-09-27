# at-food-co-ai-lead-finder-n8n
AI-powered B2B lead finder and automated notification workflow for AT Food Co. using n8n, OpenAI gpt-4o-mini, Google Sheets, and Slack API integration. Features dynamic SDR prompt templates, 10 B2B lead payloads, and human-in-the-loop email dispatch logic.
# 🐶 AT Food Co. — AI Lead Finder & n8n Automated Outreach Pipeline
> **B2B Growth Automation: Integrating No-Code Orchestration (n8n), LLMs (OpenAI), and Real-Time Slack Alerts**

[![Domain](https://img.shields.io/badge/Domain-AI%20Automation%20%7C%20B2B%20Growth-orange)](#)
[![Stack](https://img.shields.io/badge/Stack-n8n%20%7C%20OpenAI%20%7C%20Slack%20API-blue)](#)
[![Methodology](https://img.shields.io/badge/Methodology-Human--In--The--Loop%20SDR-green)](#)

---

## 📌 Executive Summary & Business Objective

* **The Challenge:** As **AT Food Co.** expands into B2B Corporate Wellness (offering fresh pet care perks and subsidized fresh meal subscriptions to pet-friendly tech offices), manual prospect research and cold SDR writing create severe operational bottlenecks.
* **The Solution:** An automated **n8n workflow** that ingests qualified B2B HR leads, generates hyper-personalized cold outreach emails using `gpt-4o-mini`, and routes formatted approval cards to Slack in real time.
* **Core Impact:** Cuts lead research and draft preparation time by **80%**, enabling a single growth marketer to review and dispatch 100+ hyper-targeted B2B pitches daily.

---

## 🏗️ Technical Architecture & Workflow Flowchart

    [Google Sheets / Webhook] ──> [OpenAI Agent Node] ──> [Slack API Connector]
     (Ingests B2B Lead Data)      (Generates Personalized  (Delivers Approval Card
                                    SDR Pitch in <60 words)   to #leads-outreach)

---

## 🔌 Node-by-Node Specification

### Node 1: Trigger & Ingestion (`n8n-nodes-base.googleSheets`)
* **Function:** Fetches prospective B2B client lists from Google Sheets or incoming HTTP Webhook payloads.
* **Payload Variables Ingested:** `Name`, `Job_Role`, `Company_Name`, `Email_Address`.

### Node 2: AI Email Generation (`n8n-nodes-base.openAi`)
* **Model Engine:** `gpt-4o-mini`
* **Execution Logic:** Injects ingested lead fields into a structured system prompt, generating a tailored 3-sentence outreach email.

### Node 3: Slack Notification Routing (`n8n-nodes-base.slack`)
* **Function:** Formats data into a rich Slack Block Kit layout and sends it to the `#leads-outreach` channel.
* **Human-in-the-Loop:** Displays an **[Approve & Dispatch]** button for instant 1-click email execution.

---

## 🤖 SDR System Prompt Template

> Act as an expert B2B sales development representative (SDR) writing personalized cold outreach emails for "AT Food Co."
>
> Product: AT Food Co. Corporate Pet Wellness Program (subsidized fresh meal packs & digital Dog Life Record perks for pet-friendly tech workplaces).
> Target Lead: {{Name}}, {{Job Role}} at {{Company Name}}.
>
> Rules:
> 1. Keep the message under 60 words.
> 2. Maintain a professional, highly relevant, and conversational tone.
> 3. Mention their specific job role and company name to make it feel personalized.
> 4. End with a soft, low-friction Call to Action (CTA).
>
> Output Format: A short 3-sentence outreach email.

---

## 📊 Qualified Lead Payload Matrix (10 Prospects)

| # | Prospect Name | Job Role | Company Name | Target Audience Segment |
| :--- | :--- | :--- | :--- | :--- |
| **1** | Rajesh Kumar | VP of Talent Acquisition | InnovateX Systems | Executive HR Leader |
| **2** | Priya Sharma | Head of Human Resources | CloudScale Technologies | Department Head |
| **3** | Amit Patel | Lead Technical Recruiter | DataFlow Solutions | Technical Recruiter |
| **4** | Sneha Verma | Talent Acquisition Manager | NextGen Software | Operations Manager |
| **5** | Vikram Malhotra | Director of People Operations | CodeCrafters Inc. | Executive Leader |
| **6** | Ananya Roy | Senior HR Business Partner | CyberShield Labs | HR Partner |
| **7** | Rohan Mehta | Hiring Manager | AgileStack Tech | Engineering Lead |
| **8** | Divya Nair | Head of Talent Experience | DevPulse Solutions | Employee Experience |
| **9** | Sanjay Gupta | VP of Human Capital | Enterprise Cloud Co. | C-Suite Executive |
| **10** | Meera Joshi | Recruitment Lead | AI Foundations Corp | Talent Acquisition Lead |

---

## 💬 Sample Output Payload & Slack Notification Card

    🚀 New B2B Lead Alert & Draft Generated!

    • Name: Rajesh Kumar
    • Role: VP of Talent Acquisition
    • Company: InnovateX Systems
    • AI Draft Pitch:
      "Hi Rajesh, I noticed you're leading talent acquisition at InnovateX Systems. 
       Many tech companies are introducing pet wellness perks to boost workplace culture 
       and retain top talent. AT Food Co. provides subsidized fresh dog nutrition plans 
       and corporate pet records—open to exploring a quick 2-minute perk overview?"

    • Workflow Status: Pending Approval [Click to Dispatch Email]

---

## ⚙️ How to Import & Run This n8n Workflow

1. Clone or download the `workflow.json` file from this repository.
2. Open your **n8n instance** (Self-hosted / n8n Cloud) and click **Import from File**.
3. Add your `OpenAI API Key`, `Google Sheets Credentials`, and `Slack OAuth Token`.
4. Trigger the workflow manually or set a Cron Schedule to execute daily.
