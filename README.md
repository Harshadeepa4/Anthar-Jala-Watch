# Anthar-Jala Watch
### Natural Resources Groundwater Monitoring Android App powered by Generative AI 

Anthar-Jala Watch is a community-driven borewell monitoring application for Android, augmented by Generative AI . It empowers farmers, residents, panchayat workers, and environmental volunteers to collectively build a living map of groundwater health in their region . The platform enables citizens to monitor, log, visualize, and act on groundwater (borewell) data across their region, serving as the authoritative reference for local water security .

---

## 01. Problem Statement 

Groundwater is one of India's most critical natural resources, yet it faces a mounting crisis driven by over-extraction, irregular rainfall, and a lack of real-time community awareness . 

### Key Challenges 
* **Rapid Depletion:** Groundwater (Anthar-Jala) levels are declining at an alarming rate across agricultural and residential zones, threatening long-term water security .
* **Delayed Failure Detection:** Farmers and households typically discover borewell failure only when pumps run dry, by which time corrective action is costly and often too late .
* **No Community System:** There is no accessible, community-based platform to collectively monitor, log, and visualize groundwater stress at a hyper-local level .
* **Information Asymmetry:** Existing data resides with government agencies and is rarely actionable for individual landowners or local governing bodies .

---

## 02. Core Vision Pillars 

* **Crowd-Sourced Data Logging:** Users log borewell attributes like depth, year of digging, current yield, and GPS anonymously and securely .
* **Intelligent Aggregation:** The app derives water stress indices per locality using GPS-based clustering and trend analysis .
* **Visual Decision Support:** A color-coded heatmap (Green / Yellow / Red) gives communities an at-a-glance view of groundwater availability .
* **AI-Powered Recharge Guidance:** Gemini-powered guides recommend context-specific DIY recharge methods based on soil type, depth, and seasonal data .
* **Proactive Community Alerts:** Push notifications warn communities of sudden water level drops, enabling pre-emptive conservation measures .

---

## 03. App Modules & User Flow 

The application is organized into four primary modules: 

| # | Module | User Actions | Output/Outcome |
|---|---|---|---|
| **1** | **Borewell Log** | Enter water depth (ft), yield (lph), digging year; GPS auto-captured . | Submission stored; contributes to regional dataset . |
| **2** | **Water Stress Map** | View heatmap; filter by season, year, depth range . | Color overlay: Green = Safe, Yellow = Caution, Red = Critical . |
| **3** | **Recharge Guide** | Browse AI-curated DIY methods; filter by soil type or depth . | Step-by-step illustrated recharge instructions . |
| **4** | **Alerts** | Opt-in to area alerts; set personal borewell thresholds . | Push notifications on level changes or community triggers . |

---

## 04. Technical Implementation 

### Mapping & Visualization 
* Google Maps SDK for Android with Heatmap Layer via the Maps Utility Library .
* Dynamic radius weighting based on borewell yield vs. depth ratio .
* Custom tile overlays for seasonal groundwater stress layers .
* Marker clustering (`MarkerClusterManager`) for dense data points .

### Location & Data Collection 
* GPS-based automatic location tagging with user permission prompts .
* Reverse geocoding to assign village / taluk identifiers .
* Offline-first data entry with background sync via WorkManager .
* Firebase Firestore for live multi-user data storage .

### GenAI Integration 
* Vertex AI (Gemini) for personalized recharge recommendations .
* Support for natural language queries like *'What recharge method suits clay soil at 200 ft?'* .
* Trend analysis model predicting seasonal depletion curves per cluster .
* Anomaly detection for sudden yield drops triggering automated alerts .

### UI Components 
* Vertical scale widget for depth visualization with an animated water level indicator .
* Material Design 3 components utilized for accessibility and consistency .
* Color-blind-safe palette for heatmap layers, fully WCAG AA tested .
* Adaptive layouts supporting phones and tablets up to 12 inches .

### Backend & Security 
* REST API built with FastAPI hosted on Google Cloud Run .
* OAuth 2.0 authentication architecture .
* Privacy protection: No personally identifiable location is stored, and GPS coordinates are fuzzed to a 500 m radius before storage .
* Security compliance: HTTPS enforced with data encrypted at rest using AES-256 .

---

## 05. Project Scope (v1.0) 

The initial release targets rural and semi-urban communities in South India, targeting Android 14 (API 26+) .

| In Scope (v1.0) | Out of Scope (v1.0) |
|---|---|
| Android mobile app (phones & tablets) | iOS application |
| Cloud backend with REST API & database | IoT / sensor hardware integration |
| Google Maps heatmap visualization | Government system integration |
| GenAI-powered recharge guide | Desktop web portal for end users |
| Push notification alert system | Multi-country / multi-language (beyond 4) |
| Internal admin moderation dashboard | Payment or subscription features |

---

## 06. Key MVP Features (v1.0) 

1. **GPS-tagged borewell data submission form** (Priority: P0-Critical) .
2. **Real-time water stress heatmap** with Google Maps displaying Green / Yellow / Red zones (Priority: P0-Critical) .
3. **User authentication** via mobile OTP (Priority: P0-Critical) .
4. **AI-powered recharge guide** with illustrated methods (Priority: P0-Critical) .
5. **Push notification alerts** for subscribed areas (Priority: P0-Critical) .
6. **Offline data entry** with automatic background sync (Priority: P0-Critical) .
7. **Privacy-safe storage** featuring location fuzzing and no household identifiers (Priority: P0-Critical) .
8. **Multilingual support** launching with English and Kannada (Priority: P0-Critical) .

---

## 07. Non-Functional Requirements 

* **Performance:** App launch time is under 3 seconds on a 2 GB RAM device . Map data loads within 4 seconds on a 4G network .
* **Scalability:** System architecture supports up to 10,000 simultaneous concurrent users without degradation .
* **Availability:** Cloud backend deployment guarantees a 99.5% monthly uptime SLA .
* **Security & Privacy:** Data encryption via AES-256 at rest and TLS 1.3 in transit . GPS location data is stored strictly at a fuzzed 500 m radius .
* **Localization Framework:** Built to support English, Kannada, Telugu, and Tamil .
* **Battery Efficiency:** Background monitoring usage consumes less than 1% battery power per hour .