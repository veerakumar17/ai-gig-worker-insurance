# AI-Powered Parametric Insurance for Gig Delivery Workers

An AI-enabled parametric insurance platform that protects food delivery partners from income loss caused by disruptions such as heavy rain, extreme heat, floods, or severe pollution.

---

## Table of Contents

1. [Overview](#overview)
2. [Problem Statement](#problem-statement)
3. [Persona](#persona)
4. [Persona Scenario](#persona-scenario)
5. [Workflow](#workflow)
6. [Weekly Premium Model](#weekly-premium-model)
7. [Parametric Triggers](#parametric-triggers)
8. [Platform Choice](#platform-choice)
9. [AI Integration](#ai-integration)
10. [Tech Stack](#tech-stack)
11. [Architecture](#architecture)
12. [Development Plan](#development-plan)
13. [Expected Impact](#expected-impact)

---

## Overview

The gig economy has rapidly expanded in India, with millions of delivery workers supporting platforms like Swiggy and Zomato. These workers depend heavily on daily deliveries for income, but environmental disruptions — heavy rain, heat waves, floods, and pollution — can significantly reduce delivery activity and cause immediate income loss.

This platform introduces a weekly income protection plan where:

- Workers subscribe and pay a small weekly premium
- The system continuously monitors environmental data
- Payouts are **automatically triggered** when disruption thresholds are met

The system combines **AI-based risk prediction**, **automated claim triggering**, and **intelligent fraud detection** to create a scalable income protection system for gig workers.

---

## Problem Statement

Food delivery workers in India face unstable income due to environmental disruptions.

**Research indicates:**
- Average hourly income ≈ ₹102/hour
- Workers typically work 9–11 hours per day
- Monthly earnings range ₹20,000 – ₹30,000 depending on city

> Sources: Times of India, NDTV, MoneyControl, LinkedIn industry insights

**Workers remain financially vulnerable because:**
- Income depends entirely on deliveries
- Bad weather reduces orders
- Road conditions become unsafe
- Workers must still cover fuel and maintenance costs

**Example impact:**

| Scenario | Deliveries | Income |
|---|---|---|
| Normal working day | 15 | ₹1,000 |
| Rain disruption day | 6 | ₹400 |
| **Income loss** | | **₹600** |

Currently, there is no dedicated insurance product protecting gig workers from short-term income disruption.

---

## Persona

**Target Persona: Food Delivery Partner**

| Attribute | Details |
|---|---|
| Name | Ravi |
| Age | 27 |
| Platform | Swiggy |
| Work hours | 9–10 hours/day, 6 days/week |
| Daily deliveries | ~15 |
| Hourly income | ≈ ₹100/hour |
| Daily income | ₹900 – ₹1,200 |
| Monthly income | ₹22,000 – ₹28,000 |

**Daily Expenses:**
- Fuel → ₹150 – ₹300
- Mobile data → ₹10 – ₹20
- Bike maintenance → ₹30 – ₹50

Net daily income after expenses can drop to **₹600 – ₹900/day**, making delivery workers highly vulnerable to income shocks.

---

## Persona Scenario

**Worker:** Ramesh | **Platform:** Swiggy / Zomato | **City:** Hyderabad

**Normal Day vs Rain Disruption:**

| | Normal Day | Rain Disruption Day |
|---|---|---|
| Hours worked | 10 | 10 |
| Deliveries | 15 | 5 |
| Income | ₹800 | ₹250 |

**Income loss = ₹550**

**Daily expenses:**
- Fuel → ₹200 | Mobile data → ₹20 | Food → ₹100
- **Total = ₹320**

On a rain day, Ramesh earns ₹250 but spends ₹320 — **he loses money instead of earning.**

**With Insurance:**

| | Amount |
|---|---|
| Weekly premium paid | ₹50 |
| Delivery income (rain day) | ₹250 |
| Insurance payout (auto-triggered) | ₹500 |
| **Final income** | **₹750** |

---

## Workflow

```
User registers on platform
        ↓
User enters delivery location and platform
        ↓
System collects environmental data from APIs
        ↓
AI model predicts disruption risk score
        ↓
User selects weekly insurance plan
        ↓
User pays weekly premium
        ↓
System monitors disruption triggers
        ↓
Trigger detected (rain / heat / pollution)
        ↓
Claim automatically initiated
        ↓
Fraud detection verification
        ↓
Instant payout processed
```

---

## Weekly Premium Model

**Typical worker earnings:**
- Hourly income ≈ ₹100 × 10 hours = ₹1,000/day
- Weekly income = ₹1,000 × 6 days = **₹6,000/week**
- Weather disruptions can reduce earnings by **₹600 – ₹1,200/week**

### Insurance Plans

| Plan | Weekly Premium | Max Weekly Payout |
|---|---|---|
| Basic | ₹20 | ₹300 |
| Standard | ₹35 | ₹600 |
| Premium | ₹50 | ₹1,000 |

> Premium ≈ 5–10% of coverage value (standard micro-insurance logic)

### 6-Week Minimum Waiting Period

Workers must pay premiums for **6 consecutive weeks** before becoming eligible for claims. Coverage becomes fully active from **Week 7 onwards**.

This prevents users from joining only when disruptions are predicted.

### Automatic Premium Deduction

Workers provide their bank account or UPI ID during registration. The system auto-debits the weekly premium to ensure uninterrupted coverage.

### Payment Failure & Grace Period

If a deduction fails due to insufficient balance:

1. A **2-day grace period** is initiated
2. Worker is notified: *"Premium payment failed. Please add balance within 2 days to continue coverage."*
3. Any disruption claim during grace period is set to **Pending** status
4. If payment succeeds within 2 days → policy reactivates → pending claim is approved and payout is processed
5. If payment fails after 2 days → **policy is cancelled**, pending claims are rejected

---

## Parametric Triggers

| Trigger | Condition | Reason |
|---|---|---|
| Heavy Rain | Rainfall > 70 mm in 24 hours | Waterlogging reduces delivery activity |
| Extreme Heat | Temperature > 42°C | Heatwaves reduce delivery operations |
| Severe Pollution | AQI > 350 | Outdoor activity becomes dangerous |
| Flood | Government flood alert or rainfall > 120 mm | Roads become impassable |

**Data Sources:**
- India Meteorological Department (IMD)
- CPCB Pollution API
- OpenWeather Air Pollution API

---

## Platform Choice

The prototype is implemented as a **Web Platform** for the following reasons:

- Faster development during hackathon
- Easy testing and demo
- Accessible via browser on both mobile and desktop
- Simpler deployment

> Future versions will include a dedicated mobile application for workers.

---

## AI Integration

### Risk Prediction

ML models predict disruption probability per delivery zone using:
- Rainfall, temperature, AQI
- Historical disruption patterns
- Delivery activity data

**Risk Level Classification:**

| Risk Score | Risk Level |
|---|---|
| 0.0 – 0.3 | 🟢 Low Risk |
| 0.3 – 0.6 | 🟡 Medium Risk |
| 0.6 – 1.0 | 🔴 High Risk |

**Examples:**
- Anna Nagar → 0.25 → Low Risk
- Velachery → 0.52 → Medium Risk
- Flood-prone zone → 0.78 → High Risk

**Models used:** Random Forest, Logistic Regression, Gradient Boosting

### Fraud Detection

AI detects suspicious claim behaviour including:

| Fraud Type | Example |
|---|---|
| GPS spoofing | Location jumps 2 km → 30 km instantly |
| Duplicate claims | Same disruption claimed multiple times |
| Abnormal patterns | 15 claims/month vs normal 2 claims/month |

**Algorithms:** Isolation Forest, anomaly detection, clustering

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | React.js + Tailwind CSS |
| Backend | Python + FastAPI |
| Machine Learning | Scikit-learn |
| Database | SQLite |
| Weather Data | India Meteorological Department API |
| Pollution Data | CPCB / OpenWeather APIs |
| Payments | Mock UPI / Razorpay sandbox |

---

## Architecture

```
+----------------------+
| Delivery Worker      |
| (Web Application)    |
+----------+-----------+
           |
           v
+----------------------+
| Frontend (React)     |
+----------+-----------+
           |
           v
+----------------------+
| Backend API          |
| FastAPI Server       |
+----------+-----------+
           |
           v
+----------------------+
| ML Risk Prediction   |
| Fraud Detection      |
+----------+-----------+
           |
           v
+----------------------+
| Premium & Claims     |
| Processing Engine    |
+----------+-----------+
           |
           v
+----------------------+
| SQLite DB + APIs     |
| Weather / Pollution  |
+----------------------+
```

---

## Development Plan

| Phase | Focus | Tasks |
|---|---|---|
| Phase 1 | Ideation | Persona definition, system architecture, README |
| Phase 2 | Core Platform | User registration, policy management, premium calculation, claims system |
| Phase 3 | Advanced Features | AI fraud detection, payout simulation, analytics dashboards |

---

## Expected Impact

This platform provides financial protection for gig delivery workers by:

- Protecting workers from sudden income loss
- Providing automated, instant payouts
- Offering affordable micro-insurance (from ₹20/week)
- Using AI-driven risk prediction for fair pricing

By combining AI risk assessment, parametric triggers, and automated payouts, the solution creates a **scalable safety net for gig economy workers** across India.
