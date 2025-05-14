# 🎯 **Robotic Arm Project Using ESP32**  
![Robotics Badge](https://img.shields.io/badge/Robotics-IoT-blue?style=flat-square)  
![ESP32 Badge](https://img.shields.io/badge/ESP32-Project-orange?style=flat-square)  
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)  

---

## 🎨 **About the Project**  
This project is focused on building a **robotic arm** powered by the versatile **ESP32 microcontroller**. With capabilities for precise motion and wireless control, this project explores the intersection of **robotics** and **IoT**.

---

### 🔍 **Key Highlights**  
- 👨‍💻 A fully programmable robotic arm.  
- 📡 Wireless control via ESP32’s built-in Wi-Fi module.  
- 🌐 IoT-ready for cloud-based functionality.

---

## 🌟 **Features**  
✨ **Wireless Control**: Operate the arm from a distance using Wi-Fi.  
⚙️ **Precision Movements**: Program tasks with high accuracy.  
🛠️ **Modular Design**: Easy assembly and customization.  
📡 **IoT Integration**: Expandable for cloud-based operations.

---

## 🧭 **Workflow Diagram**

```mermaid
flowchart TB
    %% Hardware Layer
    subgraph "Hardware Layer"
        direction TB
        ESP32["ESP32 Microcontroller"]:::hardware
        Servos["Servo Motors (joints)"]:::hardware
        PowerSupply(("Power Supply")):::hardware
    end

    %% Firmware Layer
    subgraph "Firmware Layer"
        direction TB
        WiFi["Wi-Fi Subsystem"]:::firmware
        AsyncHTTP["AsyncWebServer Module"]:::firmware
        AsyncTCP["AsyncTCP Module"]:::firmware
        WS["WebSocket Module"]:::firmware
        ServoCtl["Servo Controller Logic"]:::firmware
        RecordLogic["Recording/Playback Logic"]:::firmware
        Buffer((Record Buffer)):::storage
    end

    %% Network Layer
    subgraph "Network"
        direction TB
        AP(("Wi-Fi AP")):::network
    end

    %% Client UI Layer
    subgraph "Client UI"
        direction TB
        Browser["Browser UI (Control Panel)"]:::client
    end

    %% Connections
    PowerSupply --> ESP32
    ESP32 --> Servos
    Browser -->|HTTP| AsyncHTTP
    Browser -->|WebSocket| WS
    AsyncHTTP --> WS
    WS --> ServoCtl
    ServoCtl --> Servos
    WS --> RecordLogic
    RecordLogic --> Buffer
    RecordLogic --> ServoCtl
    RecordLogic --> WS
    WS -->|status updates| Browser
    ESP32 -.->|hosts| AP
    Browser -.->|connects to| AP

    %% Click Events
    click WiFi "https://github.com/rajtilak-2020/robotic_arm/blob/main/Robotic_Arm.ino"
    click AsyncHTTP "https://github.com/rajtilak-2020/robotic_arm/blob/main/Assets/ESPAsyncWebServer-master.zip"
    click AsyncTCP "https://github.com/rajtilak-2020/robotic_arm/blob/main/Assets/AsyncTCP-master.zip"
    click WS "https://github.com/rajtilak-2020/robotic_arm/blob/main/Robotic_Arm.ino"
    click ServoCtl "https://github.com/rajtilak-2020/robotic_arm/blob/main/Robotic_Arm.ino"
    click RecordLogic "https://github.com/rajtilak-2020/robotic_arm/blob/main/Robotic_Arm.ino"
    click Buffer "https://github.com/rajtilak-2020/robotic_arm/blob/main/Robotic_Arm.ino"
    click Browser "https://github.com/rajtilak-2020/robotic_arm/blob/main/README.md"

    %% Styles
    classDef hardware fill:#B8E1FF,stroke:#0077B6,stroke-width:1.5px,color:#003049
    classDef firmware fill:#C1FFD7,stroke:#2D6A4F,stroke-width:1.5px,color:#1B4332
    classDef network fill:#FFE066,stroke:#FFA200,stroke-width:1.5px,color:#7F4F24
    classDef client fill:#FFCCD5,stroke:#D62828,stroke-width:1.5px,color:#6A040F
    classDef storage fill:#E6CCFF,stroke:#6A4C93,stroke-width:1.5px,color:#3C096C

    class Buffer storage
    class PowerSupply hardware
    class AP network
```

---

```mermaid
graph TD
    A[Start Program] --> B[setup Function]
    B --> C[Set Pin Modes]
    B --> D[Initialize Serial Communication]
    B --> E[Start WiFi Access Point]
    B --> F[Configure Web Server]
    B --> G[Configure WebSocket Handler]

    A --> H[loop Function]
    H --> I[Clean Up WebSocket Clients]
    I --> J{Play Recorded Steps}
    J --> |Yes| K[Execute Recorded Robot Arm Steps]
    J --> |No| L[Wait for New Commands]

    F --> M[handleRoot Function]
    M --> N[Serve HTML Control Panel]

    G --> O[WebSocket Events Handler]
    O --> P[On Connect Event]
    O --> Q[Send Current Robot Arm State]
    O --> R[On Disconnect Event]
    O --> S[On Data Event]
    S --> T{Command Type}
    T --> |Move Servo| U[Update Servo Position]
    T --> |Record| V[Start or Stop Recording Steps]
    T --> |Play| W[Start or Stop Playback]

    K --> X[Gradual Movement to Initial Position]
    K --> Y[Execute Playback Sequence]
    K --> Z[Send Real-Time Updates to WebSocket]

    N --> AA[HTML Control Panel]
    AA --> AB[Sliders for Each Servo]
    AA --> AC[Buttons for Record and Play]
    AA --> AD[WebSocket Communication]
    AD --> S
```

## 💻 **Technologies Used**  
| Component         | Purpose                      |  
|-------------------|------------------------------|  
| 🧠 **ESP32**      | Microcontroller for control. |  
| 🌀 **Servo Motors**| Precise movement of joints.  |  
| 🛠️ **Arduino IDE**| Programming environment.     |  
| 📡 **Wi-Fi**      | Wireless communication.      |  

---

## 📖 **Usage**  
1. Power on the robotic arm and establish a Wi-Fi connection.  
2. Use a **web-based app**, **smartphone**, or **controller interface** to send commands.  
3. Observe the robotic arm executing tasks smoothly.  

---

## 🛡️ **License**  
This project is licensed under the [MIT License](LICENSE).  

---

## 🙌 **Acknowledgments**  
- [Er Jyoti Ranjan Nayak](https://github.com/1997Jyotiranjannayak) Sir for guiding us in this project.  
- Open-source tools for enabling smooth development.  
- Our dedicated team for collaborative efforts.  

---

### 🖼️ **Preview**  
coming soon... 
