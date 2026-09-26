The IoT-Based Fire and Gas Monitoring System is an embedded safety project developed using the LPC21xx ARM7 microcontroller. The system continuously monitors temperature and gas leakage using an LM35 temperature sensor and MQ-2 gas sensor.

When the temperature exceeds the configured threshold or gas leakage is detected, the system activates a buzzer alert. The ESP-01 Wi-Fi module sends the sensor information to the ThingSpeak cloud platform, allowing the data to be monitored remotely.

The system also provides an LCD display, keypad-based temperature setpoint configuration, RTC-based timing, and SPI EEPROM storage for permanently saving the temperature setpoint.

🎯 Objectives

Monitor temperature in real time.

Detect gas leakage or smoke.

Provide an immediate buzzer alert during dangerous conditions.

Allow the user to configure a temperature setpoint.

Store the setpoint permanently using SPI EEPROM.

Upload monitoring data to ThingSpeak.

Enable remote monitoring through Wi-Fi.

✨ Features

🌡️ Temperature monitoring using LM35

💨 Gas/smoke detection using MQ-2

🚨 Buzzer alert for dangerous conditions

📟 16×2 LCD display

⌨️ 4×4 keypad for setpoint configuration

💾 SPI EEPROM for non-volatile data storage

📶 ESP-01 Wi-Fi connectivity

☁️ ThingSpeak cloud monitoring

🕒 RTC for time management

🔌 UART communication

🔗 SPI communication

⚡ ADC-based temperature measurement

🛠️ Hardware Requirements

Component

Purpose

LPC21xx / LPC2129

Main microcontroller

LM35

Temperature sensing

MQ-2

Gas/smoke detection

ESP-01

Wi-Fi connectivity

16×2 LCD

Display

4×4 Keypad

User input

SPI EEPROM

Setpoint storage

RTC

Real-time clock

Buzzer

Alarm indication

Power Supply

System power

💻 Software Requirements

Keil µVision

Embedded C

LPC21xx ARM7 development environment

ESP-01 AT commands

ThingSpeak IoT platform

🔌 Interfaces Used

Interface

Usage

ADC

Reading LM35 temperature

UART

LPC21xx ↔ ESP-01 communication

SPI

LPC21xx ↔ EEPROM communication

GPIO

LCD, keypad, buzzer and sensor control

RTC

Timekeeping and periodic operations

Wi-Fi

Cloud communication

⚙️ Working Principle

1. Temperature Monitoring

The LM35 generates an analog voltage proportional to the surrounding temperature.

The LPC21xx ADC reads this analog voltage and converts it into a digital value. The microcontroller then calculates and displays the temperature on the LCD.

2. Temperature Alert

The user can configure a temperature setpoint using the keypad.

If:

Temperature > Setpoint

the system considers it a temperature/fire alert and activates the buzzer.

3. Gas Detection

The MQ-2 sensor monitors the environment for combustible gases and smoke.

When gas is detected, the microcontroller activates the buzzer and updates the gas status.

4. EEPROM Storage

The configured temperature setpoint is stored in SPI EEPROM.

This allows the setpoint to remain available even after the system is powered OFF and powered ON again.

5. IoT Communication

The ESP-01 Wi-Fi module communicates with the LPC21xx through UART.

The ESP-01 connects to Wi-Fi and sends sensor information to ThingSpeak.

The cloud can be used to monitor:

Temperature

Gas status

Temperature alert status

6. RTC

The RTC maintains the current date and time and is used for time-based operations in the system.

🔄 System Flow

             ┌─────────────────┐
             │    LPC21xx      │
             │    ARM7 MCU     │
             └────────┬────────┘
                      │
        ┌─────────────┼─────────────┐
        │             │             │
        ▼             ▼             ▼
     LM35           MQ-2          Keypad
 Temperature      Gas Sensor     Setpoint
        │             │             │
        └─────────────┼─────────────┘
                      │
                      ▼
                  LCD Display
                      │
                      ▼
                   Buzzer
                      │
                      ▼
                 ESP-01 Wi-Fi
                      │
                      ▼
                ThingSpeak Cloud

📂 Project Structure

IoT-Fire-Gas-Monitoring/
│
├── main.c
├── adc.c
├── adc.h
├── lm35.c
├── lm35.h
├── esp01.c
├── esp01.h
├── uart0.h
├── uart_interrupt.c
├── spi.c
├── spi.h
├── spi_eeprom.c
├── spi_eeprom.h
├── rtc.c
├── rtc.h
├── lcd.c
├── lcd.h
├── keypad.c
├── keypad.h
├── interrupt.h
├── delay.c
├── delay.h
├── types.h
│
└── Keil Project Files

📊 Data Flow

LM35 ──► ADC ──► LPC21xx ──► LCD
                       │
MQ-2 ──────────────────┤
                       │
Keypad ────────────────┤
                       │
EEPROM ◄───────────────┤
                       │
RTC ───────────────────┤
                       │
                       ▼
                    ESP-01
                       │
                       ▼
                 Wi-Fi Network
                       │
                       ▼
                 ThingSpeak

🚨 Alert Conditions

Temperature Alert

If Temperature > Setpoint
        ↓
Buzzer ON
        ↓
Temperature Alert
        ↓
ThingSpeak Update

Gas Alert

Gas Detected
      ↓
Buzzer ON
      ↓
Gas Alert
      ↓
ThingSpeak Update

📡 IoT Monitoring

The ESP-01 Wi-Fi module is used to upload sensor information to ThingSpeak.

Example cloud fields:

Field

Data

Field 1

Temperature

Field 2

Gas Status

Field 3

Temperature Alert

This provides remote access to the monitoring information through the ThingSpeak platform.

🧰 Technologies Used

Embedded C

ARM7

LPC21xx

Keil µVision

ADC

UART

SPI

GPIO

RTC

Wi-Fi

ESP-01

ThingSpeak

IoT

🎓 Skills Demonstrated

This project demonstrates practical knowledge of:

Embedded C programming

ARM7 microcontroller programming

Peripheral interfacing

ADC programming

UART communication

SPI communication

Sensor interfacing

LCD interfacing

Keypad interfacing

EEPROM data storage

RTC programming

Wi-Fi communication

IoT cloud integration

Embedded system debugging

🔮 Future Enhancements

📱 Mobile application for monitoring

📩 SMS and email alerts

🔔 Mobile push notifications

🔋 Battery backup

📈 Historical data analysis

🌐 Web-based monitoring dashboard

🔥 Automatic emergency control system

🧪 Additional gas sensors

📡 Multiple sensor nodes

👩‍💻 Project Information

Project Name: IoT-Based Fire and Gas Monitoring System

Domain: Embedded Systems & IoT

Microcontroller: LPC21xx ARM7

Programming Language: Embedded C

Development Tool: Keil µVision

Cloud Platform: ThingSpeak

⚠️ Security Note

Do not upload Wi-Fi passwords, ThingSpeak API keys, or other credentials directly to a public GitHub repository.

Use placeholders such as:

#define WIFI_SSID       "YOUR_WIFI_SSID"
#define WIFI_PASSWORD   "YOUR_WIFI_PASSWORD"
#define API_KEY         "YOUR_THINGSPEAK_API_KEY"

📜 License

This project is developed for educational and academic purposes and can be modified or extended for further embedded and IoT applications.
