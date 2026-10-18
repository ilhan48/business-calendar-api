# ⚡ BizCal API — Global Business Calendar & Deadline API

<p align="left">
  <img src="https://img.shields.io/badge/Built%20with-Rust%20%F0%9F%A6%80-orange?style=flat-square" alt="Built with Rust" />
  <img src="https://img.shields.io/badge/Latency-%3C1ms-brightgreen?style=flat-square" alt="Sub-millisecond latency" />
  <img src="https://img.shields.io/badge/Coverage-TR%20%7C%20US%20%7C%20UK%20%7C%20DE%20%7C%20NL-indigo?style=flat-square" alt="Supported Countries" />
  <img src="https://img.shields.io/badge/Status-Early%20Access%20Waitlist-fuchsia?style=flat-square" alt="Waitlist Open" />
</p>

**BizCal API** is a blazing-fast, sub-millisecond REST API built in **Rust (Axum + Tokio)** that calculates accurate business days, public holidays, and SLA deadlines across multiple countries with a single HTTP call.

Stop hand-rolling fragile holiday tables or maintaining complex calendar rules for banking, logistics, invoicing, and SLA tracking.

---

## 🚀 Join the Live Waitlist (Early Access)

We are currently onboarding early adopters with a **generous free tier**.

👉 **[Join the Live Waitlist Here →](https://ilhan48.github.io/business-calendar-api/)** *(Live API & Waitlist Portal)*

---

## ✨ Why BizCal API?

- **Deadline Math, Done Right:** Automatically skips weekends and official public holidays—including moveable feasts, lunar/Islamic holidays, and weekend substitute/observed days (US & UK bank holidays).
- **Sub-Millisecond Responses:** Powered by Rust (`Axum` + `Tokio`). All calendar rules are computed in-memory with zero external database lookups on the hot path.
- **5 Countries at Launch:**
  - 🇹🇷 **Turkey (`TR`)** — Official national holidays + religious holidays
  - 🇺🇸 **United States (`US`)** — Federal holidays with observed Monday/Friday rules
  - 🇬🇧 **United Kingdom (`UK`)** — Bank holidays with substitute day rules
  - 🇩🇪 **Germany (`DE`)** — Federal public holidays including Easter-based dates
  - 🇳🇱 **Netherlands (`NL`)** — National holidays including King's Day observance rules

---

## 🔌 API Preview

### 1. Calculate a Business Deadline (`POST /api/v1/calculate`)

Add (or subtract) business days from any start date and get a full breakdown of skipped weekends and holidays.

**Request:**
```bash
curl -X POST https://api.bizcal.dev/api/v1/calculate \
  -H "Content-Type: application/json" \
  -d '{
    "start_date": "2026-12-18",
    "country": "DE",
    "business_days": 5
  }'
```

**Response (`200 OK` · `0.2ms`):**
```json
{
  "start_date": "2026-12-18",
  "country": "DE",
  "business_days": 5,
  "deadline": "2026-12-28",
  "deadline_weekday": "Mon",
  "calendar_days": 10,
  "weekend_days_skipped": 4,
  "holidays_skipped": 1,
  "holidays": [
    {
      "date": "2026-12-25",
      "name": "Christmas Day",
      "local_name": "Erster Weihnachtstag"
    }
  ]
}
```

### 2. List Official Public Holidays (`GET /api/v1/holidays`)

Retrieve all public holidays for a given country and year:

```bash
curl "https://api.bizcal.dev/api/v1/holidays?country=TR&year=2026"
```

---

## 📂 About This Repository

This public repository hosts the **Landing Page & Waitlist UI** ([`index.html`](./index.html)) and public API documentation for **BizCal API**.  
The core Rust calculation engine and API server are maintained in a separate private repository.

---

## 📬 Contact & Early Access

Want early access or have specific country/regional calendar requirements?  
Sign up on the **[Waitlist](https://ilhan48.github.io/business-calendar-api/)** or open an issue in this repository to request a country!
