# Automatic Fish Feeder with Companion Web App

An IoT-based automatic fish feeder that dispenses a fixed portion of food on schedule and can be controlled remotely from a web app. Built as a team project at the School of Computer Science and Engineering, RV University, Bengaluru.

## Achievements

- **First Prize** in a college competition.
- **Selected for MSME Idea Hackathon 6.0** — funding application submitted and under review.

## How it works

A **Wemos D1 Mini (ESP8266)** microcontroller drives an **SG90 continuous-rotation servo**, which turns a 3D-printed **Archimedes screw** to dispense food from a hopper. The board connects over Wi-Fi to **Firebase Realtime Database**, which acts as the bridge between the hardware and a web app. Feeding can be triggered manually ("Feed Now") or on a schedule, and every feed is logged with a timestamp.

```
Web App (HTML/CSS/JS) ─► Firebase Realtime DB ◄─► ESP8266 ─► Servo ─► Screw ─► Food
```

## Features

- Manual feeding via a "Feed Now" button
- Custom feeding schedules
- Timestamped feed-history log (manual vs. scheduled)
- NTP time synchronisation for accurate scheduling (IST)
- Wi-Fi setup through a captive portal (WiFiManager)
- Device heartbeat to show online/offline status

## Repository structure

| Path | Contents |
| --- | --- |
| `code2.0/` | Arduino firmware for the ESP8266 (`code2.0.ino`) |
| `WEB/` | Companion web app (`auqafeed/`) and Firebase hosting config |
| `step files/` | STEP exports of the mechanical parts |
| `*.f3d`, `*.f3z` | Fusion 360 source CAD (enclosure, hopper, main body, screw) |
| `ESM_Project_Report_Final.pdf` | Full project report |

## Hardware

- Wemos D1 Mini (ESP8266)
- SG90 continuous-rotation servo (signal on pin D5)
- 3D-printed hopper, Archimedes screw, and enclosure
- 5V power supply

## Tools and tech

- Arduino IDE / C++
- Autodesk Fusion 360
- Firebase Realtime Database + Hosting
- HTML, CSS, JavaScript

## Setup

**Firmware (`code2.0/code2.0.ino`)**
1. Open in the Arduino IDE and install: `FirebaseESP8266`, `NTPClient`, `WiFiManager`, and the ESP8266 board package.
2. Set `FIREBASE_HOST` to your Realtime Database URL and `FIREBASE_AUTH` to your own database secret.
3. Flash the board. On first boot it creates a Wi-Fi hotspot named **"AquaFeed Setup"** — connect to it and enter your Wi-Fi credentials.

**Web app (`WEB/auqafeed/`)**
1. Replace the Firebase config in `assets/js/script_v2.js` with your own project's config.
2. Serve the folder locally, or deploy with `firebase deploy` using the included hosting config.

> **Security note:** The `FIREBASE_AUTH` value in the firmware is a placeholder (`YOUR_FIREBASE_DATABASE_SECRET`). Never commit your real database secret. The web `apiKey` is a public Firebase web key and is safe to include; protect your data with Firebase security rules.

## Team

Developed collaboratively by a five-member team under the guidance of Prof. Shouvik Chakraborty, School of Computer Science and Engineering, RV University.
