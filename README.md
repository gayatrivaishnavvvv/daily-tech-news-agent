# 🚀 Daily Tech News Research Agent

An automated AI-powered news aggregation workflow built with **n8n**, **Groq LLM**, **TechCrunch RSS Feed**, and **Discord Webhooks**.

The workflow fetches the latest tech news daily, summarizes articles using AI, categorizes them, compiles a report, and automatically posts it to a Discord channel.

---

## 📌 Features

- Automated daily execution
- Fetches latest articles from TechCrunch RSS feed
- Filters articles published within the last 24 hours
- AI-powered categorization
- AI-generated concise summaries
- Aggregates multiple news items
- Generates Discord-friendly markdown reports
- Automatically posts reports to Discord

---

## 🏗️ Workflow Architecture

```text
Schedule Trigger
       │
       ▼
   RSS Feed Read
       │
       ▼
      Filter
       │
       ▼
 Basic LLM Chain
(Categorize + Summarize)
       │
       ▼
    Aggregate
       │
       ▼
 Final AI Compiler
       │
       ▼
 Discord Webhook
```

---

## ⚙️ Workflow Nodes

### 1. Schedule Trigger

Runs every day at 7:00 AM.

**Purpose:**
- Starts the workflow automatically.

---

### 2. RSS Feed Read

**Source:**

https://techcrunch.com/feed/

**Purpose:**
- Retrieves the latest articles from TechCrunch.

---

### 3. Filter

Filters articles published in the last 24 hours.

**Condition:**

```javascript
$json.isoDate > $now.minus({ hours: 24 })
```

---

### 4. Basic LLM Chain

**Model:** `llama-3.1-8b-instant`

**Provider:** Groq

**Tasks:**

- Categorize article into:
  - AI
  - Cybersecurity
  - Software
  - Hardware

- Generate a concise one-sentence summary.

**Output Example:**

```text
Category: AI | Summary: OpenAI launched a new enterprise AI platform.
```

---

### 5. Aggregate

Combines all summarized articles into a single collection.

---

### 6. Final AI Compiler

**Model:** `llama-3.1-8b-instant`

Creates a Discord-friendly report:

- Markdown formatted
- Maximum 1900 characters
- Intelligent truncation if needed

---

### 7. Discord Webhook

Posts the final report directly to a Discord channel.

---

## 🤖 AI Models Used

| Purpose | Model |
|----------|---------|
| News Categorization | llama-3.1-8b-instant |
| News Summarization | llama-3.1-8b-instant |
| Final Report Generation | llama-3.1-8b-instant |

Provider: **Groq**

---

## 📰 Categories Supported

- AI
- Cybersecurity
- Software
- Hardware

---

## 📷 Workflow Screenshot

Add your workflow screenshot here:

```markdown
![Workflow](screenshots/workflow.png)
```

---

## 📊 Example Output

```markdown
🚀 DAILY TECH NEWS RESEARCH REPORT 🚀

━━━━━━━━━━━━━━

🤖 AI
• OpenAI released new reasoning models.

🔐 Cybersecurity
• Researchers discovered a major vulnerability.

💻 Software
• GitHub launched new Copilot features.

⚙️ Hardware
• Nvidia unveiled next-generation AI chips.

━━━━━━━━━━━━━━
End of Report
```

---

## 🛠️ Tech Stack

- n8n
- Groq API
- TechCrunch RSS Feed
- Discord Webhooks
- Llama 3.1 8B Instant

---

## 🚀 Setup

### 1. Import Workflow

Import the provided `workflow.json` into n8n.

### 2. Configure Groq Credentials

Add your Groq API key inside n8n credentials.

### 3. Configure Discord Webhook

Replace:

```text
YOUR_DISCORD_WEBHOOK_URL
```

with your Discord webhook URL.

### 4. Activate Workflow

Enable the workflow and let it run automatically.

---

## 🔒 Security Notes

Before uploading to GitHub:

- Remove Groq API credentials
- Remove Discord webhook URLs
- Do not expose secrets publicly

---

## 📁 Project Structure

```text
daily-tech-news-agent/
│
├── README.md
├── workflow.json
│
└── screenshots/
    └── workflow.png
```

---

## 🎯 Future Improvements

- Multiple RSS sources
- Email notifications
- Telegram integration
- Slack integration
- News deduplication
- Sentiment analysis
- Historical news storage
- Trend analysis dashboard

---

## 📄 License

MIT License

---

## 👩‍💻 Author

Built using n8n, Groq, RSS feeds, and Discord automation to deliver daily AI-powered technology news reports.