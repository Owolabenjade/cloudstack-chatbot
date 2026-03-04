# CloudStack AI Chatbot - Portfolio Project

An intelligent customer support chatbot system built to solve common B2B support challenges.

![CloudStack Demo](https://img.shields.io/badge/Status-Business%20Project-blue)
![Tools](https://img.shields.io/badge/Tools-Tawk.to%20%7C%20n8n%20%7C%20HubSpot%20%7C%20Slack-green)

---

## 🎯 Project Overview

**Client:** CloudStack SaaS (A B2B Project Management Software)

**Problem:** Single support specialist handling 150-200 chat inquiries/week, with 15-20 minute response times and missed enterprise leads.

**Solution:** AI-powered chatbot that:
- Handles 50%+ of inquiries automatically
- Qualifies leads and routes VIPs to sales
- Integrates with CRM for automatic contact creation
- Sends real-time Slack alerts for urgent matters

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| **Tawk.to** | Chat widget + triggers + shortcuts |
| **n8n** (Railway) | Workflow automation |
| **HubSpot CRM** | Contact & deal management |
| **Slack** | Team notifications |
| **GitHub Pages** | Site hosting |

---

## 📊 Features

### 1. Intelligent Chat Widget
- Pre-chat form captures visitor info
- Automated welcome messages (triggers)
- Quick response shortcuts for common questions
- Business hours awareness

### 2. Lead Qualification
- Captures: Company size, use case, timeline, decision role
- Automatic VIP detection (200+ employees)
- Routes hot leads to sales team

### 3. Smart Routing & Alerts
- **VIP Leads** → #vip-leads Slack + HubSpot Deal
- **Standard Leads** → #chatbot-leads Slack + HubSpot Contact
- **Support Requests** → #support-queue Slack
- **Churn Risk** → #churn-risk Slack (when "cancel" mentioned)

### 4. CRM Integration
- Automatic contact creation in HubSpot
- Custom properties for qualification data
- Deal creation for enterprise leads

---

## 🏗️ Architecture

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   Visitor   │────▶│   Tawk.to   │────▶│    n8n      │
│  (Website)  │     │  (Chat Bot) │     │ (Workflows) │
└─────────────┘     └─────────────┘     └──────┬──────┘
                                               │
                    ┌──────────────────────────┼──────────────────────────┐
                    │                          │                          │
                    ▼                          ▼                          ▼
             ┌─────────────┐           ┌─────────────┐           ┌─────────────┐
             │   HubSpot   │           │    Slack    │           │    Slack    │
             │  (Contacts) │           │ #vip-leads  │           │  #support   │
             └─────────────┘           └─────────────┘           └─────────────┘
```

---

## 📁 Project Structure

```
cloudstack-chatbot/
├── index.html          
├── config.js               
├── .gitignore          
├── README.md           
```

---

## 🚀 Setup Instructions

### Prerequisites
- Tawk.to account
- HubSpot account
- Slack workspace
- Railway account

### Quick Start

1. **Clone the repository**
   ```bash
   git clone https://github.com/YOUR_USERNAME/cloudstack-chatbot.git
   cd cloudstack-chatbot
   ```

2. **Create config.js**
   ```javascript
   const CONFIG = {
       TAWK_PROPERTY_ID: 'your-tawk-property-id',
       TAWK_WIDGET_ID: 'your-tawk-widget-id',
       N8N_BASE_URL: 'https://your-n8n-instance.up.railway.app'
   };
   ```

3. **Open index.html in browser**
   - Chat widget should appear in bottom-right corner

---

## 📈 Results & Metrics

| Metric | Before | After (Projected) |
|--------|--------|-------------------|
| Bot Deflection Rate | 0% | 50%+ |
| Avg. First Response | 15-20 min | <30 sec (bot) |
| Support Hours/Day | 6+ hours | 2-3 hours |
| Lead Capture Rate | ~10/week | 25+/week |
| Missed Enterprise Leads | 2-3/month | 0 |

---

## 🔧 n8n Workflows

### Workflow 1: New Lead Handler
- **Trigger:** Webhook `/new-lead`
- **Actions:** Create HubSpot contact → Check if VIP → Send Slack alert

### Workflow 2: Support Ticket Handler
- **Trigger:** Webhook `/support-ticket`
- **Actions:** Send Slack alert to #support-queue

### Workflow 3: Churn Alert Handler
- **Trigger:** Webhook `/churn-alert`
- **Actions:** Send Slack alert to #churn-risk

### Workflow 4: Daily Summary
- **Trigger:** Schedule (6 PM daily)
- **Actions:** Send summary to #chatbot-daily

---

## 🔒 Security Considerations

- All sensitive credentials securely stored
- Webhook URLs not exposed in public code
- Test files excluded from repository
- No API keys hardcoded in source

---

## 👤 Author

**Your Name**
- LinkedIn: [linkedin.com/in/benjaminowolabi](https://linkedin.com/in/benjaminowolabi)
- GitHub: [@owolabenjade](https://github.com/owolabenjade)

---

## 🙏 Acknowledgments

- CloudStack SaaS is based on common B2B support challenges
- Built following automation best practices
- A real-world chatbot implementations