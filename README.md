# 🚗 Smart Parking System

## 📌 Project Overview

The **Smart Parking System** is an IoT-enabled parking management project designed to monitor parking-slot occupancy and provide a convenient web-based parking interface.

The system combines an **ESP32 microcontroller**, **IR sensors**, **LED indicators**, **Firebase**, and a **Next.js web application** to monitor parking slots and manage reservations.

The project is designed to reduce manual parking management, provide real-time slot status, and support reservation-based parking.

---

## 👨‍💻 Project Information

| Field | Details |
|---|---|
| **Project Title** | Smart Parking System |
| **Student Name** | Vanijain |
| **USN** | 1JS23EC174 |
| **Domain** | Internet of Things (IoT) / Web Application |
| **Microcontroller** | ESP32 |
| **Database / Backend Service** | Firebase |
| **Frontend** | Next.js / React |
| **Language(s)** | TypeScript, JavaScript, C/C++ |
| **Development Platform** | VS Code / Arduino IDE or PlatformIO |

---

## 🎯 Objectives

- Monitor parking-slot occupancy automatically.
- Detect vehicles using IR sensors.
- Display available and occupied slots through a web interface.
- Provide a simple parking reservation workflow.
- Connect the physical parking hardware with the cloud/web application.
- Improve parking management and reduce manual monitoring.
- Provide a foundation for future smart-city and IoT parking applications.

---

## ⚙️ System Architecture

```text
                 ┌─────────────────────┐
                 │     User / Admin     │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │  Next.js Web App    │
                 │ Parking Dashboard   │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │      Firebase       │
                 │ Database / Services │
                 └──────────┬──────────┘
                            │
                     Wi-Fi / Internet
                            │
                            ▼
                 ┌─────────────────────┐
                 │        ESP32        │
                 │   IoT Controller    │
                 └──────┬───────┬──────┘
                        │       │
                 ┌──────▼───┐ ┌─▼─────────┐
                 │ IR Sensor│ │ LED Status │
                 │  Sensors │ │ Indicators │
                 └──────────┘ └────────────┘
```

---

## 🔧 Hardware Components

| Component | Purpose |
|---|---|
| **ESP32 Development Board** | Main IoT controller and Wi-Fi communication |
| **IR Sensors** | Detect vehicle presence in parking slots |
| **LEDs** | Indicate slot availability/occupancy |
| **220Ω / 330Ω Resistors** | Current limiting for LEDs |
| **Breadboard / PCB** | Hardware prototyping and connections |
| **Jumper Wires** | Component interconnection |
| **5V / USB Power Supply** | Power for the ESP32 and prototype |

> **Note:** Each LED should be connected through a suitable current-limiting resistor, such as **220Ω or 330Ω**.

---

## 🔌 ESP32 & Circuit Section

The ESP32 acts as the central controller for the hardware portion of the project.

### Basic Connections

```text
IR Sensor 1  ─────► ESP32 GPIO
IR Sensor 2  ─────► ESP32 GPIO
IR Sensor 3  ─────► ESP32 GPIO
     │
     └──── Vehicle Detection

ESP32 GPIO ──► 220Ω/330Ω ──► LED ──► GND
```

### IR Sensor Operation

When a vehicle is detected in front of an IR sensor:

```text
Vehicle Detected
       │
       ▼
IR Sensor Changes State
       │
       ▼
ESP32 Reads Sensor
       │
       ▼
Slot Status Updated
       │
       ▼
LED / Web Dashboard Updated
```

### ESP32 Firmware

The ESP32 firmware is located in:

```text
scripts/esp32_sensor/
```

Before uploading the firmware, configure your Wi-Fi credentials locally. **Do not commit real Wi-Fi passwords to GitHub.**

---

## 💻 Software Stack

### Frontend

- **Next.js**
- **React**
- **TypeScript**
- HTML / CSS
- Responsive web interface

### Backend / Cloud

- **Firebase**
- Firebase database/services
- Firebase security rules

### IoT

- **ESP32**
- C/C++
- Wi-Fi communication
- IR sensor input
- LED output

### Development Tools

- Visual Studio Code
- Arduino IDE / PlatformIO
- Git
- GitHub

---

## 🌐 Web Application

The web application provides the parking management interface.

Typical functionality includes:

- User authentication
- Parking-slot dashboard
- Slot availability indication
- Reservation/booking workflow
- OTP-based booking flow
- Reservation countdown
- Slot cancellation
- Real-time status updates

### Parking Slot Status

```text
┌───────────────┐
│   SLOT 01     │
│   AVAILABLE   │
└───────────────┘

┌───────────────┐
│   SLOT 02     │
│    OCCUPIED   │
└───────────────┘
```

---

## 🔐 Security

This repository intentionally excludes sensitive configuration files.

Do **not** upload:

```text
.env
.env.local
.env.production
serviceAccountKey.json
firebase-adminsdk-*.json
```

Use environment variables for Firebase and other private configuration.

A sample environment configuration can be maintained using:

```text
.env.example
```

Never commit real API secrets, service-account credentials, Wi-Fi passwords, or private keys.

---

## 📸 Project Screenshots

Add project screenshots to a folder such as:

```text
screenshots/
├── login-page.png
├── parking-dashboard.png
├── booking-popup.png
├── slot-status.png
├── esp32-circuit.png
└── hardware-prototype.png
```

Then add them to this README using:

```markdown
## 📸 Screenshots

### Login Page
![Login Page](screenshots/login-page.png)

### Parking Dashboard
![Parking Dashboard](screenshots/parking-dashboard.png)

### Booking / OTP
![Booking](screenshots/booking-popup.png)

### ESP32 Hardware Prototype
![ESP32 Hardware](screenshots/esp32-circuit.png)
```

---

## 📁 Project Structure

```text
smart-parking-main/
│
├── app/                  # Next.js application pages
├── components/           # Reusable UI components
├── context/              # Application contexts
├── hooks/                # Custom React hooks
├── lib/                  # Firebase and utility functions
├── scripts/
│   └── esp32_sensor/     # ESP32 firmware
├── types/                # TypeScript types
│
├── firestore.rules       # Firebase security rules
├── package.json          # Project dependencies/scripts
├── package-lock.json     # npm dependency lock file
├── pnpm-lock.yaml        # pnpm lock file
├── .env.example          # Example environment configuration
├── .gitignore
└── README.md
```

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
cd smart-parking-main
```

### 2. Install dependencies

Using npm:

```bash
npm install
```

### 3. Configure environment variables

Create a local `.env.local` file using `.env.example` as a reference.

```bash
cp .env.example .env.local
```

On Windows, you can also create `.env.local` manually.

Enter your Firebase configuration in `.env.local`.

### 4. Start the development server

```bash
npm run dev
```

Open the local development URL shown by Next.js, normally:

```text
http://localhost:3000
```

### 5. ESP32 setup

1. Open the ESP32 firmware in `scripts/esp32_sensor/`.
2. Select the correct ESP32 board.
3. Configure the required GPIO pins.
4. Enter your local Wi-Fi credentials.
5. Connect the ESP32 using USB.
6. Upload the firmware.
7. Open Serial Monitor to verify sensor readings and Wi-Fi connectivity.

---

## 🔄 Working Principle

```text
START
  │
  ▼
ESP32 Initializes
  │
  ▼
Connect to Wi-Fi
  │
  ▼
Read IR Sensors
  │
  ▼
Vehicle Detected?
  │
 ┌┴─────────────┐
 │              │
YES             NO
 │              │
 ▼              ▼
Mark Slot      Mark Slot
Occupied       Available
 │              │
 └──────┬───────┘
        ▼
Update System / Dashboard
        │
        ▼
User Can Book Available Slot
        │
        ▼
OTP Generated
        │
        ▼
Reservation Timer
        │
        ▼
END / Slot Released
```

---

## 🔮 Future Scope

- Increase the number of parking slots.
- Add mobile application support.
- Add QR-code based entry and exit.
- Integrate payment gateways.
- Add automatic number-plate recognition.
- Add parking analytics and usage reports.
- Add administrator monitoring and reports.
- Integrate additional sensors for more reliable vehicle detection.
- Deploy the system for larger smart-city parking facilities.

---

## 📚 Project Documentation

This repository contains the implementation of the Smart Parking System. Additional project documentation such as circuit diagrams, project reports, presentation slides, and test results can be added under:

```text
docs/
```

---

## 👨‍🎓 Author

**Vanijain**  
**USN:** 1JS23EC174

Engineering Project – Smart Parking System

---

## ⭐ Acknowledgement

This project was developed as an academic IoT project integrating embedded systems, cloud services, and web technologies to demonstrate a practical smart-parking solution.

---

## 📜 License

This project is intended primarily for academic and educational purposes. Add an appropriate open-source license if you intend to distribute or reuse the project publicly.
