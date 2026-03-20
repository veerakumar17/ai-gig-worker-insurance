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
10. [AI-Based Plan Recommendation System](#ai-based-plan-recommendation-system)
11. [Payment Failure, Grace Period & Risk-Based Interest System](#payment-failure-grace-period--risk-based-interest-system)
12. [Fraud Detection & Adversarial Defense System](#fraud-detection--adversarial-defense-system)
13. [Tech Stack](#tech-stack)
14. [Architecture](#architecture)
15. [Development Plan](#development-plan)
16. [Expected Impact](#expected-impact)

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

### Dynamic Premium Calculation

The platform uses a risk-based pricing model where the weekly premium is dynamically adjusted based on the worker's delivery zone risk level.

**Risk Multipliers:**

| Risk Level | Multiplier |
|---|---|
| 🟢 Low Risk | 0.9 |
| 🟡 Medium Risk | 1.0 |
| 🔴 High Risk | 1.2 |

**Formula:** `Final Premium = Base Premium × Risk Multiplier`

**Example (Premium Plan — ₹50 base):**

| Risk Level | Calculation | Final Premium |
|---|---|---|
| 🟢 Low Risk | ₹50 × 0.9 | ₹45 |
| 🟡 Medium Risk | ₹50 × 1.0 | ₹50 |
| 🔴 High Risk | ₹50 × 1.2 | ₹60 |

> Maximum premium is capped to ensure affordability and prevent overcharging in high-risk scenarios.

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
4. If payment succeeds within 2 days → policy remains active → pending claim is approved and payout is processed  
5. If payment is not completed after 2 days → **policy remains active with a risk-based daily interest penalty applied**, pending claims continue to remain in **Pending** state until payment is completed  
6. Once balance is available → system auto-deducts **pending premium + accumulated interest** → policy becomes fully active and pending claims are processed
   
---

## Payment Failure, Grace Period & Risk-Based Interest System

If automatic premium deduction fails due to insufficient balance, a 2-day grace period is initiated.

### Grace Period (First 2 Days)

- Worker is notified to add balance
- Policy remains temporarily active
- Any disruption during this period → Claim marked as **Pending**

### Post Grace Period (After 2 Days)

- Policy is **not** cancelled
- A risk-based daily interest penalty is applied
- The system continuously monitors user account balance

### Risk-Based Interest Model

Interest is dynamically calculated based on the user's risk profile.

**Formula:** `Interest = Premium × Risk Rate × Delay Days`

**Final Payable:** `Total Amount = Premium + (Premium × Risk Rate × Delay Days)`

| Variable | Description |
|---|---|
| Premium (P) | Weekly premium amount |
| Risk Rate (R) | Based on user risk level |
| Delay Days (D) | Number of days after grace period |

**Risk Levels & Interest Rates:**

| Risk Level | Interest Rate (per day) |
|---|---|
| 🟢 Low Risk | 1% (0.01) |
| 🟡 Medium Risk | 2% (0.02) |
| 🔴 High Risk | 3% (0.03) |

**Risk Determination** — Risk level is calculated using:
- Historical claim behavior
- Fraud risk score
- Payment reliability
- Activity patterns

> Higher risk users → Higher penalty

### Interest Calculation Examples

**Weekly Premium = ₹50, Delay = 3 days**

| Risk Level | Calculation | Interest | Total Payable |
|---|---|---|---|
| 🟢 Low Risk (1%) | 50 × 0.01 × 3 | ₹1.5 | ₹51.5 |
| 🟡 Medium Risk (2%) | 50 × 0.02 × 3 | ₹3 | ₹53 |
| 🔴 High Risk (3%) | 50 × 0.03 × 3 | ₹4.5 | ₹54.5 |

### Auto-Deduction System

Once balance is available, the system automatically deducts:
- Pending premium
- Accumulated interest

> Fully automated — no manual payment required.

### Claim Handling During Pending Period

If a disruption occurs during the grace period or interest (pending) period:
- Claim is recorded as **Pending**

After successful payment (premium + interest):
- Policy becomes active
- Pending claims are validated and processed

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

**Models used:** Random Forest

### Fraud Detection

AI detects suspicious claim behaviour including:

| Fraud Type | Example |
|---|---|
| GPS spoofing | Location jumps 2 km → 30 km instantly |
| Duplicate claims | Same disruption claimed multiple times |
| Abnormal patterns | 15 claims/month vs normal 2 claims/month |

**Algorithms:** Isolation Forest, anomaly detection, clustering

### AI-Based Plan Recommendation System

The platform uses a hybrid AI architecture combining Machine Learning and LLaMA3 to provide intelligent, personalized insurance plan recommendations based on each worker's real-world conditions.

**How It Works:**

1. **User Input** — Worker provides weekly salary and current location
2. **Weather Data Integration** — Real-time weather data is fetched via OpenWeather API and factored into risk evaluation
3. **Risk Prediction (ML)** — A trained Random Forest model predicts a risk score (0–1) → Low / Medium / High
4. **AI Recommendation (LLaMA3)** — The risk score, salary, and weather conditions are passed to LLaMA3, which suggests the most suitable plan with a human-readable explanation

**Role of LLaMA3:**

LLaMA3 handles intelligent decision-making and personalized recommendations. It does **not** perform risk prediction — it enhances interpretability and user experience by explaining the selected plan in plain language.

**Recommendation Logic (Hybrid Approach):**

| Step | Component | Role |
|---|---|---|
| 1 | ML Model | Predicts risk score |
| 2 | Rule-Based Constraints | Ensures affordability (avoids expensive plans for low-salary users) |
| 3 | LLaMA3 | Final recommendation with explanation |

---

## Fraud Detection & Adversarial Defense System

The system uses an AI-powered, multi-layer fraud detection engine to identify and prevent malicious activities such as GPS spoofing, duplicate claims, bot behavior, and coordinated fraud attacks.

Instead of relying on a single signal, the platform combines location intelligence, behavioral analytics, device fingerprinting, and graph-based fraud detection.

### Fraud Detection Overview

| Fraud Type | Description | Detection Logic | Example |
|---|---|---|---|
| 📍 GPS Spoofing | Fake location injection using spoofing apps | Compare GPS vs motion sensors vs IP location | Location jumps from 2 km → 30 km instantly |
| 🔁 Duplicate Claims | Same disruption claimed multiple times | Claim pattern matching + timestamp validation | Same incident claimed repeatedly |
| 📉 Abnormal Patterns | Unusual claim frequency or activity | Behavioral baseline deviation detection | 15 claims/month vs normal 2/month |

### Multi-Source Location Verification

The system validates user location using multiple independent signals:
- GPS coordinates
- IP-based location
- Device motion sensors (accelerometer, gyroscope)

**Detection Logic:**
- If GPS changes but no physical movement detected → flagged
- If GPS ≠ IP location mismatch → flagged

> Prevents fake location injection (GPS spoofing attacks)

### Behavioral Analysis Engine

Each user has a dynamic behavioral profile built over time.

**Tracked Parameters:**
- Speed patterns
- Delivery frequency
- Active working hours
- Route consistency

**Detects:**
- Unrealistic travel speeds
- Continuous 24/7 activity (bot behavior)
- Repetitive identical routes

> Identifies non-human or scripted activity

### Device Fingerprinting

Each device is uniquely identified using:
- Device ID
- OS version
- App version
- Hardware-level signals

**Detects:**
- Multiple accounts using same device
- Frequent device switching

> Prevents multi-account fraud

### Fraud Ring Detection (Graph-Based Intelligence)

The system builds a relationship graph between users using:
- Shared IP addresses
- Shared devices
- Synchronized activity patterns

**Detects:**
- Clusters of coordinated users
- Organized fraud rings

> Critical for detecting large-scale coordinated fraud attacks

### Real-Time Risk Scoring Engine

Each user action is evaluated using a dynamic risk score.

**Formula:** `Risk Score = Location Risk + Behavior Risk + Device Risk + Network Risk`

**Risk Weights:**

| Factor | Score |
|---|---|
| Location mismatch | +30 |
| Abnormal behavior | +20 |
| Device reuse | +40 |
| Fraud cluster match | +50 |

**Decision Engine:**

| Score Range | Action |
|---|---|
| 0 – 30 | ✅ Allow |
| 30 – 70 | ⚠️ Monitor |
| 70+ | 🚫 Block |

### Algorithms Used

**1. Isolation Forest**
- Detects anomalies in GPS movement, claim frequency, and behavioral deviations
- Works well for outlier detection in large datasets

**2. Clustering (DBSCAN / K-Means)**
- Groups users based on device similarity, IP patterns, and behavior
- Identifies fraud rings & coordinated attacks

**3. Rule-Based Validation**
- Detects deterministic fraud: impossible speeds, location mismatch, duplicate claims
- Provides instant validation (low latency)

**4. Behavioral Profiling**
- Compares current activity vs historical patterns
- Detects subtle deviations over time

### Fairness & False Positive Protection

To ensure genuine users are not affected:
- First anomaly → Warning
- Repeated anomalies → Temporary restriction
- High-confidence fraud → Block

> Manual review available for edge cases. Adaptive thresholds applied to reduce false positives.

### Defense-in-Depth Architecture

This system is designed so that no single signal decides fraud — multiple layers combine to reach a final decision, ensuring high accuracy, real-time detection, and scalability for production systems.

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
