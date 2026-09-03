# LunaBot System Architecture

## 1. Overview

LunaBot is a ROS 2-based autonomous robotic system designed for navigation, environmental monitoring, and routine patrol operations inside simulated lunar habitat environments.

The system follows a modular architecture in which navigation, perception, habitat monitoring, mission management, and user-interface components operate as independent modules while communicating through ROS 2.

The architecture is designed around three primary goals:

* Autonomous and safe navigation
* Continuous habitat condition monitoring
* Risk-aware mission decision-making

---

## 2. High-Level Architecture

```text
                ┌─────────────────────────┐
                │      LunaBot UI         │
                │ Monitoring & Controls   │
                └────────────┬────────────┘
                             │
                             ▼
                ┌─────────────────────────┐
                │    Mission Manager      │
                │ Patrol / Risk Priority  │
                └────────────┬────────────┘
                             │
          ┌──────────────────┼──────────────────┐
          ▼                  ▼                  ▼
 ┌────────────────┐ ┌────────────────┐ ┌────────────────┐
 │   Navigation   │ │ Habitat Monitor│ │   Perception   │
 │   & Planning   │ │ Temp / O2 etc. │ │ Camera/Sensors │
 └───────┬────────┘ └───────┬────────┘ └───────┬────────┘
         │                  │                  │
         └──────────────────┼──────────────────┘
                            ▼
                 ┌──────────────────────┐
                 │   ROS 2 Middleware   │
                 │ Topics / Nodes / TF  │
                 └──────────┬───────────┘
                            ▼
                 ┌──────────────────────┐
                 │ Robot / Simulation   │
                 │ Lunar Habitat World  │
                 └──────────────────────┘
```

---

## 3. Core Modules

### Mission Management

The mission-management layer coordinates LunaBot's patrol behaviour and determines which habitat zone requires attention.

Instead of treating every patrol location equally, the system can use environmental information and predefined risk values to prioritize mission targets.

This provides the foundation for risk-aware autonomous patrol.

### Autonomous Navigation

The navigation layer is responsible for moving LunaBot between mission targets while avoiding obstacles.

The navigation architecture is designed to support:

* Map-based navigation
* Robot localization
* Global path planning
* Local obstacle avoidance
* Goal-based autonomous movement

ROS 2 navigation components provide the foundation for this functionality.

### Habitat Monitoring

The habitat-monitoring module processes environmental parameters associated with different habitat zones.

Examples include:

* Temperature
* Oxygen level
* Habitat-zone status
* Environmental warnings

Abnormal conditions can influence mission priority and trigger alerts.

### Perception

The perception layer provides information about the robot's surroundings.

The complete LunaBot architecture is designed to incorporate:

* LiDAR
* Camera
* IMU
* Odometry

These sensor sources support localization, obstacle detection, environmental awareness, and future sensor-fusion improvements.

### User Interface

The LunaBot interface provides a human-readable view of robot operations.

The interface is designed to display information such as:

* Robot and mission status
* Environmental readings
* Current patrol target
* Risk information
* Camera feed
* Navigation/control information

This allows astronauts or habitat operators to supervise the autonomous robot without continuously controlling it.

---

## 4. ROS 2 Communication Architecture

LunaBot uses ROS 2 as the communication backbone between independent software modules.

ROS 2 enables the system to separate navigation, monitoring, perception, mission logic, and visualization into modular nodes.

This architecture provides:

* Modularity
* Easier debugging
* Independent component development
* Expandability
* Hardware and simulation integration

---

## 5. Risk-Aware Mission Layer

A key architectural feature of LunaBot is the separation between **navigation** and **mission-level decision making**.

Traditional navigation answers:

> "How should the robot reach the selected destination safely?"

LunaBot additionally considers:

> "Which destination should the robot attend to first?"

Environmental readings and habitat risk information can therefore influence patrol priority before a navigation goal is selected.

This transforms the robot from a simple waypoint-following platform into the foundation of an autonomous habitat-support system.

---

## 6. System Workflow

```text
Environmental / Sensor Data
            ↓
     Habitat Monitoring
            ↓
      Risk Evaluation
            ↓
     Mission Prioritization
            ↓
      Target Selection
            ↓
    Autonomous Navigation
            ↓
     Obstacle Avoidance
            ↓
      Zone Inspection
            ↓
   Status / Alert / UI Update
            ↓
       Continue Patrol
```

---

## 7. Design Philosophy

LunaBot follows a modular and extensible design so that simulation components can later be replaced by physical sensors and hardware without redesigning the entire software architecture.

The current prototype therefore acts as a foundation for progressively integrating autonomous navigation, environmental sensing, perception, risk assessment, and robotic maintenance capabilities for future lunar habitats.

