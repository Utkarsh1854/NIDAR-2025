# NIDAR 2025: Autonomous Disaster Management Drone

NIDAR (Networked Intelligent Drone for Airborne Rescue) is an autonomous unmanned aerial vehicle (UAV) platform engineered for real-time search and rescue (SAR) operations in GPS-denied or hazardous disaster environments. The system leverages high-performance edge AI for live human detection and autonomous flight control to assist first responders when every second counts.

<!-- Place a 3-second looping GIF or high-quality image of the drone/detection interface here -->
![NIDAR 2025 System Demo](docs/assets/system_demo.gif)

---

## 🚀 Key Features
* **Real-Time Edge AI Detection:** Onboard human target identification using optimized deep learning models.
* **Autonomous Flight Control:** Intelligent path planning and localized navigation built for unstable, complex environments.
* **Low-Latency Telemetry:** Robust data streaming pipeline transmitting live video feeds and target coordinates back to the ground control station (GCS).

---

## 🛠️ System Architecture

The NIDAR platform splits processing workloads between high-level edge intelligence and low-level flight stabilization to ensure deterministic, safe execution.

```mermaid
graph TD
    A[Onboard Camera / Sensors] -->|Live Video Feed| B[NVIDIA Jetson Xavier NX]
    B -->|YOLOv8 Inference| C{Human Detected?}
    C -->|Yes: Extract Coordinates| D[Target Mapping & GCS Alert]
    B -->|Navigation Commands| E[Flight Controller / Pixhawk]
    E -->|PWM Control Signals| F[Brushless Motors & Actuators]
    
    style B fill:#2c3e50,stroke:#3498db,stroke-width:2px,color:#fff
    style E fill:#2c3e50,stroke:#e74c3c,stroke-width:2px,color:#fff
