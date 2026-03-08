# Habit75: A Data-Driven 75-Day Challenge Tracker

**Habit75** is a high-performance iOS application designed to quantify the "75-Day Challenge". By bridging the gap between qualitative user logs and quantitative biometric sensor data, the app provides a unified dashboard for longitudinal habit analysis.

## Project Overview

**Habit75** implements a tiered challenge system (**Hard, Medium, and Soft**) that adapts to different user intensities. The core mission is to transform "discipline" into "measurable data" through automated tracking and persistence.

### Key Technical Pillars

* **Automated ETL Pipeline:** Real-time extraction of biometric data (Steps, Active Energy, Hydration) via **HealthKit**.
* **Local-First Persistence:** High-speed data management using **SwiftData** to ensure 100% offline functionality and data privacy.
* **Time-Series Visualization:** Dynamic progress monitoring using **Apple Charts** to correlate activity trends over a 75-day cycle.

---

## Technical Architecture

### Data Engineering & Schema

The application utilizes a normalized relational schema to manage complex 75-day datasets. Each `DayEntry` object functions as a central node, linking multiple data streams:

1. **Biometric Stream:** Automated pulls from the HealthKit Store (Quantitative).
2. **Habit Stream:** User-validated task completion logs (Qualitative).
3. **Multimedia Stream:** Progress photo metadata and daily reading/meal logs.

### The "Consistency" Algorithm

The app calculates a **Completion Metric** for every 24-hour window. This logic validates if a user has met all specific constraints of their selected tier (e.g., "Hard Challenge" requires two 45-minute workouts and 1 gallon of water) before marking a day as "Perfect" in the history log.

---

## Application Modules

### 1. The Challenge Dashboard

The central command center where users track their current streak, daily tasks, and water intake.

* **Visual Check:** Real-time progress bars for hydration goals.
* **Tier Logic:** Displays unique requirements based on the Hard, Medium, or Soft selection.

### 2. Health Insights (Data Visualization)

A dedicated analytics view that transforms raw logs into insights.

* **Workout Heart Rate:** Time-series line charts of cardiovascular intensity.
* **Weekly Consistency:** Bar charts aggregating total habit adherence across a 7-day rolling window.

### 3. 75-Day History

A comprehensive audit trail of every day in the challenge.

* **Success Metrics:** Tracks "Perfect Days" and total completion percentage.
* **Data Persistence:** Uses **SwiftData** to provide instant access to historical logs without server-side latency.

---

## Privacy & Data Integrity

* **On-Device Processing:** All personal health data is processed locally; no data is transmitted to external servers.
* **HealthKit Compliance:** Adheres to Apple’s strict data privacy standards, requiring explicit user authorization for all biometric read/write operations.

---

## Tech Stack

* **Language:** Swift 6.0
* **Frameworks:** SwiftUI, SwiftData, HealthKit, Apple Charts
* **Minimum Deployment:** iOS 26.0
* **Architecture:** MVVM (Model-View-ViewModel)

---

## Support & Documentation

For technical inquiries or support, please refer to our [Support Gist](https://gist.githubusercontent.com/shaswat28/892f5e6c3cc4393107b4794585ec7a66/raw/a83a354b2e115caecd103c5b35a285ac51f749e6/Support%2520Habit75).

**Developed by Shaswat Sharma**
