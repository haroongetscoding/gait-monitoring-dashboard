# Gait Monitoring Dashboard

Single-file web dashboard for an ESP32 + MPU6050 wearable gait-monitoring prototype. It visualises detected gait events (possible freezing of gait and other gait anomalies), sensory-cue status, device health, and session summaries.

> Academic proof-of-concept for gait-event monitoring. **Not intended for medical diagnosis or treatment.**

## Run it

No build step and no dependencies — just open the file in a browser:

```
start "Gait Monitoring Dashboard.html"
```

Or serve it locally:

```
npx serve .
```

## Pages

| Page | What it shows |
| --- | --- |
| Overview | KPI cards, events-by-time chart, wearable device status, recent events |
| Real-Time Monitoring | Live monitoring state, current system state, event feed, workflow diagram |
| Gait Events | Filterable table of recorded events with a detail drawer |
| Session Analysis | Session timeline, event distribution, events over session |
| Device Status | ESP32 / sensor / Wi-Fi / Firebase / cue / battery state |
| Settings | Placeholder |

## Data flow

```
MPU6050 → ESP32 → movement processing → on-device gait anomaly detection → vibration cue
ESP32 → Wi-Fi → Firebase → dashboard (detected events only)
```

Movement processing and detection run locally on the ESP32; only detected-event information is sent to Firebase. Event data in this build is mock/static.

## Stack

Plain HTML + CSS + vanilla JS in one file, inline SVG charts, `prefers-color-scheme` dark mode, responsive layout (sidebar collapses below 820px).
