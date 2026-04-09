# CLAUDE.md: Next-Gen Family Disaster Dashboard
**"From Static Hazard Maps to Dynamic Evacuation Routing."** A real-time disaster support system specialized for Local Municipality.

## 1. System Architecture
This project utilizes a hybrid data storage configuration based on a secure Google Cloud infrastructure.
* **Ingestion (GAS)**: Polls Template-based Email Parser for Disaster Alerts (5-minute intervals).
* **Real-time Layer (Firebase RTDB)**: Synchronizes current active fires and family locations in milliseconds.
* **Analytics/Persistence Layer (Google Sheets)**: Permanently stores the complete history from fire ignition to containment.
* **Dashboard (Streamlit)**: Statistics and analysis based on the Google Sheets data source.

## 2. Tech Stack
* **Android (Kotlin)**:
* `Jetpack Compose`, `maps-compose`
* `FusedLocationProviderClient` (Location Sharing)
* `Activity Recognition API` (Power optimization via stillness detection)
* `Firebase Auth` (Closed operation via Google Sign-In)

* **Backend (Google Apps Script)**:
* `Secret Manager` (Protection of Service Account keys)
* `LockService` (Concurrency control for Google Sheets)
* `OAuth2 for Apps Script` (Secure Firebase communication)

* **Storage/Infrastructure**:
* `Firebase Realtime Database` (RTDB)
* `Google Sheets API` (Historical DB)
* `Google Cloud Secret Manager`

## 3. Core Design Principles
### ① Security and Privacy
* **Closed Circle**: Access is restricted to authenticated family members only via Firebase Security Rules.
* **Sharing Toggle**: A physical toggle in the app to completely disable location sharing during normal times.
* **Principle of Least Privilege**: Uses a Service Account from GAS, narrowing permissions to specific database paths.
### ② Performance and Power Optimization
* **Stillness Detection**: Suppresses GPS updates when the user is stationary (15-min intervals) and upgrades to high-accuracy mode (1-min intervals) upon movement detection.
* **Purple Alert Circles**: Fire areas are rendered in Purple (alpha 0.2–0.3) to avoid confusion with traffic congestion (Red).
### ③ Analytics and Insights
* **Analysis Metrics**: Time to containment, fire density by area, and occurrence trends by time of day.
* **Matching Logic**: Currently uses address strings, with plans to migrate to coordinate-based (lat/lng) and timestamp proximity matching.