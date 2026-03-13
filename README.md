# ai-gig-worker-insurance
AI-powered parametric insurance platform protecting food delivery partners from income loss caused by disruptions like heavy rain, extreme heat, floods, or pollution. The system uses AI-based risk assessment to set weekly premiums and automatically triggers payouts when disruption thresholds are detected.

1. Project Title
AI-Powered Parametric Insurance for Gig Delivery Workers

An AI-enabled parametric insurance platform that protects food delivery partners from income loss caused by disruptions such as heavy rain, extreme heat, floods, or severe pollution.

2. Overview
The gig economy has rapidly expanded in India, with millions of delivery workers supporting platforms like Swiggy and Zomato.

These workers depend heavily on daily deliveries for income. However, environmental disruptions such as heavy rain, heat waves, floods, and pollution can significantly reduce delivery activity, resulting in immediate income loss.

This project introduces an AI-powered parametric insurance platform where workers subscribe to a weekly income protection plan. The platform continuously monitors environmental data and automatically triggers payouts when disruption conditions are met.

The system combines:

AI-based risk prediction

dynamic premium calculation

automated claim triggering

intelligent fraud detection

to create a scalable income protection system for gig workers.

3. Problem Statement
Food delivery workers in India face unstable income due to environmental disruptions.

Research indicates:

Average hourly income ≈ ₹102/hour

Workers typically work 9–11 hours per day

Monthly earnings range ₹20,000 – ₹30,000 depending on city

Sources include Times of India, NDTV, MoneyControl and LinkedIn industry insights.

Despite working long hours, workers remain financially vulnerable because:

income depends entirely on deliveries

bad weather reduces orders

road conditions become unsafe

workers must still cover fuel and maintenance costs

Example:

Normal working day
15 deliveries → ₹1000 income

Rain disruption day
6 deliveries → ₹400 income

Income loss = ₹600 in a single day

Currently, there is no dedicated insurance product protecting gig workers from short-term income disruption.

4. Persona
Target Persona: Food Delivery Partner
Example Worker Profile

Name: Ravi
Age: 27
Platform: Swiggy Delivery Partner

Work Pattern
Works 9–10 hours/day

Works 6 days/week

Completes around 15 deliveries daily

Earnings
Average hourly income ≈ ₹100/hour

Daily income ≈ ₹900 – ₹1200

Monthly income ≈ ₹22,000 – ₹28,000

Daily Expenses
Fuel → ₹150 – ₹300
Mobile data → ₹10 – ₹20
Bike maintenance → ₹30 – ₹50

Net daily income after expenses can drop to ₹600 – ₹900/day.

This makes delivery workers vulnerable to income shocks.

5. Persona Scenario
Delivery Worker Scenario
Name: Ramesh
Platform: Swiggy / Zomato
City: Hyderabad

Work Pattern:

Works 10–12 hours/day

Works 6–7 days/week

Monthly income ₹20,000 – ₹30,000

Rain Disruption Example
Normal day

10 working hours
15 deliveries
Income = ₹800

Rain disruption day

5 deliveries
Income = ₹250

Income loss:

₹800 − ₹250 = ₹550

Expenses
Fuel → ₹200
Mobile data → ₹20
Food → ₹100

Total expenses → ₹320

Income that day = ₹250
Expenses = ₹320

Ramesh loses money instead of earning.

Insurance Support
Ramesh subscribes to a weekly protection plan.

Weekly premium = ₹50

If rainfall exceeds threshold, the platform automatically triggers payout.

Example payout:

₹500 sent instantly via UPI

Final income that day:

₹250 delivery income + ₹500 insurance payout = ₹750

6. Workflow
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
Trigger detected (rain/heat/pollution)
↓
Claim automatically initiated
↓
Fraud detection verification
↓
Instant payout processed

7. Weekly Premium Model
Typical worker earnings:

Hourly income ≈ ₹100
Daily work ≈ 10 hours

Daily income = ₹1000

Weekly income:

₹1000 × 6 days = ₹6000/week

Weather disruptions can reduce earnings by ₹600–₹1200/week.

Insurance Plans
| Plan     | Weekly Premium | Max Weekly Payout |
| -------- | -------------- | ----------------- |
| Basic    | ₹20            | ₹300              |
| Standard | ₹35            | ₹600              |
| Premium  | ₹50            | ₹1000             |
Premium follows common micro-insurance logic:

Premium ≈ 5–10% of coverage value

Example:

Weekly income = ₹6000
Premium = ₹35

If disruption occurs:

Loss = ₹1200
Insurance payout = ₹600

8. Parametric Triggers
Heavy Rain
Trigger condition:

Rainfall > 70 mm in 24 hours

Reason: Waterlogging reduces delivery activity.

Extreme Heat
Trigger condition:

Temperature > 42°C

Reason: heatwaves reduce delivery operations.

Severe Pollution
Trigger condition:

AQI > 350

Reason: outdoor activity becomes dangerous.

Data source:

CPCB Pollution API
OpenWeather Air Pollution API

Flood
Trigger condition:

Government flood alert
or rainfall > 120 mm

Weather data can be sourced from India Meteorological Department (IMD).

9. Platform Choice
The prototype is implemented as a Web Platform.

Reasons:

faster development during hackathon

easy testing and demo

accessible via browser on both mobile and desktop

simpler deployment

Future versions can include a mobile application for workers.

10. AI Integration
Risk Prediction (Machine Learning)
Machine learning models predict disruption probability in each delivery zone.

Features used:

rainfall

temperature

AQI

historical disruption patterns

delivery activity

Example output:

Disruption Probability = 0.75

Risk Level Classification
The ML model outputs a risk score between 0 and 1.
| Risk Score | Risk Level  |
| ---------- | ----------- |
| 0.0 – 0.3  | Low Risk    |
| 0.3 – 0.6  | Medium Risk |
| 0.6 – 1.0  | High Risk   |
Example:

Anna Nagar → 0.25 → Low Risk
Velachery → 0.52 → Medium Risk
Flood-prone zone → 0.78 → High Risk

ML models used:

Random Forest

Logistic Regression

Gradient Boosting

Dynamic Premium Calculation
Premium adjusts based on predicted risk.

Example formula:
premium = base_price + (risk_score × risk_multiplier)
Example:

premium = 20 + (0.7 × 20)

Final premium ≈ ₹34

Workers in safer zones pay lower premiums.

Fraud Detection
AI detects suspicious claim behaviour.

Examples:

GPS spoofing
Example: location jump 2 km → 30 km instantly

Duplicate claims
Same disruption claimed multiple times

Abnormal claim patterns
Example: 15 claims/month vs normal 2 claims/month

Algorithms used:

Isolation Forest

anomaly detection

clustering

11. Tech Stack
Frontend
React.js + Tailwind CSS

Backend
Python + FastAPI

Machine Learning
Scikit-learn

Database
SQLite

External APIs

Weather data → India Meteorological Department
Pollution data → CPCB / OpenWeather APIs

Payments

Mock UPI / Razorpay sandbox

12. Architecture

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

13. Development Plan


Phase 1 – Ideation
define persona

system architecture

README documentation

Phase 2 – Core Platform
user registration

insurance policy management

premium calculation

claims system

Phase 3 – Advanced Features
AI fraud detection

payout simulation

analytics dashboards

14. Expected Impact
This platform provides financial protection for gig delivery workers.

Benefits:

protects workers from sudden income loss

provides automated payouts

affordable micro-insurance

AI-driven risk prediction

By combining AI risk assessment, parametric triggers, and automated payouts, the solution creates a scalable safety net for gig economy workers.


