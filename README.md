# ⚠️🚨 MAINTENANCE MODE - DO NOT USE 🚨⚠️

> **🛑 THIS PROJECT IS CURRENTLY UNDER MAINTENANCE**
>
> **DO NOT USE THIS BOT RIGHT NOW!**
>
> SheerID has updated their fraud detection systems. Using this bot at the moment may result in:
> - ❌ Your account being **flagged for fraud**
> - ❌ Permanent **bans** from SheerID verification
> - ❌ Loss of access to student discounts
>
> **We are working on updates to improve detection bypass. Check back later for updates.**
>
> _Last updated: January 2026_

---

## 📢 Join Our Community

> **💬 For updates, discussions, and more:**
> 
> 👉 **Join our Telegram channel:** [t.me/RootLayerR](https://t.me/RootLayerR)
>
> Stay connected for the latest news, feature updates, and community support!

---

# 🎭 Verification Bot | Tyrell's Edition 🚀

![Status](https://img.shields.io/badge/Status-🔧%20Maintenance-orange)
![Python](https://img.shields.io/badge/Python-3.11+-blue)
![License](https://img.shields.io/badge/License-MIT-purple)
![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)

A high-performance, asynchronous Telegram bot engineered for industrial-grade **Student Verification**. Featuring a sophisticated credit economy, multi-layered anti-detection, and a powerful real-time web administration suite.

---

## 🌟 Elite Features

### 🤖 Core Automation Logic
- **Precision Flow:** Fully automated SheerID interaction—from university selection to dynamic document generation and secure upload.
- **Global FIFO Queue:** A centralized First-In-First-Out orchestration system that manages load, prevents rate-limiting, and ensures fair processing.
- **Hyper-Fast Core:** Built on `asyncio` and `httpx` for massive concurrency and non-blocking performance.
- **Smart Retry Logic:** S3 uploads retry up to 3 times with exponential backoff for reliability.

### 💰 Automated Economy
- **Smart Credit System:**
  - **Welcome Gift:** New users automatically receive **3 credits**.
  - **Fair Usage:** Verifications cost **1 credit**. 
  - **Safety Net:** Credits are **auto-refunded** instantly if a verification fails for technical reasons.
- **Viral Referral System:**
  - Every user gets a unique invite link.
  - Earn **+2 credits** immediately when your referral completes their first session.
- **Redeemable Vouchers:** Generate unique codes with custom credit values, usage limits, and expiration dates.

### 🛡️ Multi-Layer Anti-Detection
- **Browser Spoofing:** Dynamic rotation of premium User-Agents (Chrome 131+, Firefox, Edge, Safari).
- **Header Intelligence:** Precise SheerID header emulation with correct lowercase ordering and Client-Hints.
- **TLS Fingerprinting:** `curl_cffi` integration to mimic real browser TLS handshakes, bypassing advanced fraud detection.
- **Resilient Fallbacks:** Intelligent library switching (`curl_cffi` → `cloudscraper` → `httpx`) ensures continuity.
- **Human-Like Delays:** Random timing with occasional "thinking" pauses to avoid bot detection.

### 📄 Advanced Document Generation
- **Realistic Data (Faker):** Uses Python's Faker library for unlimited unique names and birth dates.
- **Randomized Transcripts:** Each document has different courses pulled from 9 departments (45+ courses).
- **Variable GPA:** GPA ranges from 2.9 to 3.95 instead of a suspicious static value.
- **Major Field:** 20 realistic majors randomly assigned to each student.
- **University-Specific IDs:** Student ID formats match each university's actual pattern.
- **Dynamic Semester:** Automatically shows "SPRING" or "FALL" based on current date.

### 🔍 Self-Healing Proxy Engine
- **Active Monitoring:** A background worker rigorously tests every proxy every 30 minutes.
- **Delay Tolerance:** Optimized for slow proxies with a **15-second warm-up grace period** and 3-stage retry logic.
- **Automatic Quarantine:** Proxies that fail 5 consecutive checks are marked as "Dead" and auto-quarantined.
- **Smooth Recovery:** Dead proxies are continually tested and brought back online the moment they become healthy.

### 🛡️ Data Protection
- **Auto-Backup:** Every hour, all data files are automatically zipped and sent to your Telegram.
- **Manual Backup/Restore:** Admin panel allows download and upload of data backups.
- **Ephemeral-Ready:** Designed for Render's ephemeral filesystem with backup safety nets.

### 🎛️ Command-Center (Admin Panel)
- **Stealth Access:** Protected by a secret URL path (`/YOUR_SECRET_ROUTE`) and encrypted password.
- **Global Analytics:** Instantly view total users, circulating credits, and lifetime verification throughput.
- **Error Breakdown:** Track specific error types (Submit Failed, API Error, Upload Failed, etc.).
- **Per-User Dossier:** Track individual success/fail rates, referral history, and registration dates.
- **Proxy Health Dashboard:** Real-time monitoring of all proxies with status, failures, and last check time.
- **Broadcast Pulse:** Send stylized Markdown announcements to your entire user base at once.
- **Voucher Studio:** Real-time management and creation of credit codes.
- **User Management:** Manually update user credits from the admin panel.

---

## 🚀 Deployment (Render Free-Tier Optimized)

### 1️⃣ Prepare Environment
- Fork this repository to your GitHub.
- Create a **Web Service** on [Render.com](https://render.com).
- Connect your fork.

### 2️⃣ Service Configuration
- **Runtime:** `Python 3`
- **Build Command:** `pip install -r requirements.txt`
- **Start Command:** `python bot.py`

### 3️⃣ Vital Environment Variables 🔑
| Variable | Mandatory? | Description |
| :--- | :---: | :--- |
| `TELEGRAM_BOT_TOKEN` | **YES** | Get from [@BotFather](https://t.me/botfather). |
| `ADMIN_PASSWORD` | **YES** | Password for the web admin dashboard. |
| `ADMIN_ROUTE` | **YES** | The secret path (e.g. `panel777`). Avoid simple words like `admin`. |
| `FLASK_SECRET_KEY` | **YES** | Keeps you logged in. Generate with `secrets.token_hex(32)`. |
| `PROXIES_JSON` | No | A single-line JSON array: `["socks5://user:pass@host:port", "..."]` |
| `KEEP_ALIVE_URL` | No | Your app URL (e.g. `https://my-bot.onrender.com`) to prevent sleep. |

---

## 📁 Directory Structure

```plaintext
├── bot.py                # The "Brain" (Telegram API & Flask Dashboard)
├── script.py             # The "Engine" (Core verification & Document Logic)
├── anti_detect.py        # The "Shield" (Headers, Fingerprints, User-Agents)
├── requirements.txt      # Dependencies
├── .env                  # Secrets configuration
├── stats.json            # Aggregated global success/fail analytics
├── users.json            # User database (Credits/Referrals)
├── codes.json            # Active credit voucher database
└── daily.json            # Daily usage limits tracking
```

---

## 📦 Dependencies

```
python-telegram-bot>=20.0    # Telegram API
httpx[socks]>=0.25.0         # HTTP client with SOCKS support
flask>=3.0.0                 # Admin dashboard
python-dotenv>=1.0.0         # Environment config
Pillow>=10.0.0               # Document image generation
curl_cffi>=0.6.0             # TLS fingerprint spoofing
cloudscraper>=1.2.0          # Cloudflare bypass
faker>=22.0.0                # Realistic data generation
```

---

## 🎮 Bot Commands

| Command | Action |
| :--- | :--- |
| `/start` | Launch the interactive main menu and check your balance. |
| `/redeem <CODE>` | Claim a credit voucher. |

---

## 📊 Background Workers

| Worker | Interval | Function |
| :--- | :--- | :--- |
| Verification Queue | Continuous | Processes FIFO verification jobs |
| Auto-Backup | 1 hour | Sends data backup to admin Telegram |
| Keep-Alive | 5 minutes | Pings service URL to prevent sleep |
| Proxy Health | 30 minutes | Tests and quarantines unhealthy proxies |
| Broadcast | 5 seconds | Checks for pending announcements |

---

## 💡 Success Pro-Tips

1. **Quality Proxies:** Use high-quality Residential or SOCKS5 proxies for the highest success rates.
2. **Persistence:** If verification fails due to "Submit Failed," wait 5 minutes—the credits were refunded, so you can try again!
3. **Admin Monitoring:** Keep an eye on the **Proxy Health** table in the dashboard; if many are "Dead," it's time to rotate your proxy list.
4. **Regular Backups:** Auto-backup sends to your Telegram every hour, but you can also manually download from the admin panel.

---

## 🔄 Recent Updates (v2.0)

- ✅ **Faker Integration:** Unlimited realistic names and dates
- ✅ **Randomized Courses:** 45+ courses across 9 departments
- ✅ **Variable GPA:** No more static 3.85
- ✅ **Major Field:** Added to transcripts
- ✅ **Dynamic Semester:** Auto-detects SPRING/FALL
- ✅ **S3 Retry Logic:** 3 attempts with exponential backoff
- ✅ **Auto-Backup:** Hourly zip to admin Telegram
- ✅ **curl_cffi Support:** Better TLS fingerprinting
- ✅ **Human-Like Delays:** Occasional longer pauses

---

## ⚠️ Legal Disclaimer

This software is provided "as is" for educational and research purposes only. The developers do not endorse or encourage any unauthorized use of external services. Users assume all responsibility for compliance with local laws and service terms.

---

**Crafted with ❤️ by Tyrell 🎭**
