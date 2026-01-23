# SmartEcho Home

## Overview
SmartEcho Home is a **local smart-home cyber-physical system** built on a Raspberry Pi using **Z-Wave sensors**, **Z-Way Server**, **Node-RED**, and **InfluxDB**. The project collects real-time sensor readings, processes them through Node-RED logic, displays them in a user-friendly dashboard with notifications, and supports exporting/storing data for analysis.

---

## Features

### Functional Requirements
- **Sensor Integration (Z-Wave):** Include and manage sensors using Z-Way SmartHome UI.
- **Data Ingestion:** Read sensor values (vDev IDs and metrics) and process them in Node-RED.
- **Dashboard Monitoring:** Display live sensor values (gauges, charts, and status indicators).
- **Notifications & Logging:** Trigger alerts for critical events (leak, motion, smoke) and maintain a notification log.
- **Data Export:** Download sensor data as CSV for reporting and offline analysis.
- **(Optional) Database Storage:** Write sensor data to a time-series database for historical tracking.

### Non-Functional Requirements
- **Performance:** Responsive local dashboard with continuous updates.
- **Usability:** Simple UI for non-technical users (clear status + alerts).
- **Scalability:** Supports adding more Z-Wave sensors and additional metrics.
- **Reliability:** Local operation without depending on cloud services.

---

## Project Phases
1. **Phase 1 — Setup & Sensor Inclusion**
   - Configure Raspberry Pi, install Z-Way, host SmartHome UI, include sensors.
2. **Phase 2 — Node-RED Data Processing**
   - Extract sensor IDs from SmartHome UI and implement logic to read/normalize data.
3. **Phase 3 — Dashboard & Notifications**
   - Build Node-RED dashboard pages, notification rules, and event log.
4. **Phase 4 — Database & Storage**
   - Design InfluxDB structure (buckets/measurements) and store sensor readings.

---

## System Architecture (Short)
- **Sensors (Z-Wave):** Smoke, leak/flood, motion/vibration, air quality, smart plug  
- **Gateway:** Z-Way controller + Z-Way server creates virtual devices (vDevs)
- **Processing:** Node-RED reads vDev metrics, normalizes values, applies alert rules
- **Visualization:** Node-RED Dashboard shows live status and notification history
- **Storage (optional):** InfluxDB stores time-series readings and supports export

---

## Repository Structure
```plaintext
smart-echo-home/
├── README.md
├── Diagrams/
│   ├── Component_diagram.jpeg
│   └── Sequence_diagram.png
├── Flow_Screenshots/
│   ├── Air_quality_sensor_flow.png
│   ├── Leak_sensor_flow.png
│   ├── Motion_sensor.png
│   ├── Plug.png
│   └── Smoke_sensor.png
├── Images_dashboard/
│   └── (dashboard screenshots)
├── final_dashboard_flow/
│   └── final_node-RED_dashboard.json
├── individual_sensor_flows/
│   ├── Air_quality.json
│   ├── flood_sensor.json
│   ├── smoke_sensor.json
│   ├── Motion_sensor.json
│   └── Smart_Plug.json
└── sample_data_downloaded/
    └── all_sensors_today.csv
```
---
## How to Run (Short)
### Prerequisites
- Raspberry Pi with Z-Way Server running and sensors included
- Node-RED installed and running on the Pi
- (Optional) InfluxDB if database export/storage is enabled

### Steps
1. Open Node-RED editor: `http://<pi-ip>:1880`
2. Import the final flow:
   - `final_dashboard_flow/final_node-RED_dashboard.json`
3. Click **Deploy**
4. Open dashboard: `http://<pi-ip>:1880/dashboard`

---

## Usage
- Use the dashboard to monitor:
  - **Air quality** (temperature, humidity, CO2/VOC if available)
  - **Leak sensor** (water leak state + tamper/battery)
  - **Smoke sensor** (alarm states + temperature + battery)
  - **Motion/Vibration** (motion/alarm + seismic/acceleration if available)
  - **Smart plug** (power/energy + on/off control if configured)
- Notifications appear on the dashboard and are logged for traceability.
- Exported CSV example is provided in `sample_data_downloaded/`.

---

## Visuals
- Architecture diagrams: `Diagrams/`
- Node-RED flow screenshots: `Flow_Screenshots/`
- Dashboard UI screenshots: `Images_dashboard/`

---

## Team / Responsibilities (Optional)
Phase distribution:
- Phase 1: Setup + Z-Way + sensor inclusion
- Phase 2: Node-RED ingestion + normalization logic
- Phase 3: Dashboard + notifications + event log + export UI
- Phase 4: InfluxDB design + storage + validation queries

---

## Project Repository
**Note:** The complete project implementation is available in the GitLab repository.

---

## Project Status
Completed core pipeline of the project and succeeded in making the dashboard, but there is always scope for improvements, and this project can be worked on further for improvements in automation.
