# 📩 GitHub Trending Daily Digest with n8n

Automatically fetch the latest **GitHub Trending repositories**, clean the data, and send a nicely formatted **daily email digest** — powered by n8n.

## ✨ Features

- Scrapes GitHub Trending page daily
- Extracts repository details:
  - ✅ Name
  - ✅ Link
  - ✅ Description
  - ✅ Language
  - ✅ Stars
- Converts data to **HTML email digest**
- Sends results via Email (Gmail/SMTP/other)
- Subject line auto-includes today’s date (e.g., `GitHub Trending (2025-08-18)`)

------

## 🛠️ Setup Instructions

1. **Import Workflow**

   - Clone this repo or copy the JSON workflow into your n8n instance.

2. **Configure Trigger**

   - Use a Cron node (e.g., run every morning).

3. **Email Setup**

   - Update your Email node with SMTP/Gmail credentials.

   - Subject can be dynamic:

     ```
     Github Trending ({{ $now.format("YYYY-MM-DD") }})
     ```

4. **Optional Customizations**

   - Change email formatting in the `Build Email HTML` Function node.
   - Adjust the scraping target if GitHub modifies its HTML.
   - Add Slack/Discord/Webhook nodes if you prefer messages instead of email.

------

## 📸 Example Output

<img width="1061" height="594" alt="image" src="https://github.com/user-attachments/assets/e1b5fb0c-5fe5-489a-b229-6e1bfcfc94c6" />


------

## 📂 Workflow Overview

```
flowchart TD
  A[Cron Trigger] --> B[HTTP Request GitHub Trending]
  B --> C[Clean HTML Function]
  C --> D[Extract Repos Function]
  D --> E[Build Email HTML Function]
  E --> F[Email Node]
```

------

## 🚀 Use Cases

- Daily GitHub discovery newsletter
- Internal dev team updates
- Inspiration feed for new projects

------

## 📜 License

MIT License — feel free to use, modify, and share.
