# 🚀 Instagram Reels Automation (AI + n8n)

## 📌 Overview

This project is a fully automated **content generation and publishing system** built using **n8n**.

It automatically:

* Fetches trending videos from TikTok
* Filters them based on specific criteria
* Avoids duplicate content
* Generates viral captions using AI
* Publishes videos as Instagram Reels

> ⚡ The goal: build a **hands-free content machine** for social media growth.

---

## 🧠 How It Works

The workflow runs daily and follows this pipeline:

1. **Fetch Videos**

   * Uses TikTok API (via RapidAPI)
   * Retrieves videos based on a niche (e.g. fitness motivation)

2. **Split & Process**

   * Converts API response into individual video items

3. **Filter Content**

   * Duration between 20–40 seconds
   * Contains specific keywords (e.g. `#gym`)

4. **Pick Video**

   * Selects a random video to diversify content

5. **Clean Data**

   * Extracts only required fields:

     * `video_id`
     * `video_url`

6. **Duplicate Detection**

   * Checks Google Sheets for existing video IDs

7. **Decision Logic**

   * If duplicate → fetch another video
   * If new → continue workflow

8. **Store Data**

   * Saves video ID in Google Sheets (prevents reposting)

9. **Generate Caption (AI)**

   * Uses LLM (OpenRouter / OpenAI)
   * Creates short, viral captions with hashtags

10. **Publish to Instagram**

    * Creates media container (Meta Graph API)
    * Waits for processing
    * Publishes Reel automatically

---

## 🛠️ Tech Stack

* **n8n** – Workflow automation
* **TikTok Scraper API (RapidAPI)** – Video sourcing
* **OpenRouter / OpenAI** – AI caption generation
* **Google Sheets** – Duplicate tracking
* **Meta Graph API** – Instagram publishing

---

## ⚙️ Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/instagram-reels-automation.git
```

---

### 2. Import Workflow into n8n

* Open n8n
* Go to **Workflows → Import**
* Paste the JSON file

---

### 3. Configure Credentials

You must connect:

#### 🔑 RapidAPI

* Add your API key in the TikTok node

#### 📊 Google Sheets

* Connect your Google account
* Create a sheet with column:

  * `video_id`

#### 🤖 AI Model

* Add OpenRouter or OpenAI credentials

#### 📱 Meta (Instagram Graph API)

* Connect your Facebook Developer App
* Add:

  * Instagram Business Account ID
  * Access Token

---

### 4. Customize the Workflow

You can modify:

* Keywords:

```text
@motivationaltrained
```

* Filters:

  * Duration
  * Hashtags

* Posting time:

  * Default: daily at 8 PM

---

## 🔁 Duplicate Handling Logic

This system prevents reposting:

* Each video ID is stored in Google Sheets
* Before posting:

  * If ID exists → skipped
  * If not → posted and saved

> ⚠️ Note: Random selection + API results may still occasionally repeat.
> For production, consider iterating over all items instead of random selection.

---

## ⚠️ Limitations

* TikTok API reliability depends on RapidAPI plan
* Instagram Graph API has strict rate limits
* Requires Instagram Business Account
* Media must be publicly accessible via URL

---

## 🚀 Future Improvements

* Post multiple videos per day
* Smart scheduling (based on engagement time)
* AI video editing (subtitles, hooks)
* Content categorization (gym, mindset, etc.)
* Telegram/Discord monitoring bot

---

## 💡 Use Cases

* Social media automation agencies
* Faceless content pages
* Growth hacking experiments
* AI-powered content pipelines

---

## 📜 License

This project is for educational and experimental purposes.

---

## 🤝 Contributing

Feel free to fork, improve, and submit pull requests.

---

## ⭐ Support

If you found this useful:

* Star the repo ⭐
* Share it with others
* Build something even cooler 🚀
