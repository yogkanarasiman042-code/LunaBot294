# 🌙 LunaBot

### Risk-Aware Autonomous Navigation and Habitat Monitoring Robot for Lunar Habitats using ROS 2

LunaBot is a ROS 2-based autonomous robotic system designed to support future lunar habitats through autonomous navigation, environmental monitoring, risk-aware patrol and operator supervision.

Instead of simply following a fixed patrol sequence, LunaBot introduces a **risk-aware mission layer** that can prioritize habitat zones based on environmental conditions and operational importance.

## 🚀 The Problem

Future lunar habitats require continuous inspection and monitoring. Astronaut time is extremely valuable, while habitat conditions such as oxygen level, temperature and equipment status can require rapid attention.

A conventional patrol robot can navigate to predefined destinations, but it does not necessarily determine **which location requires attention first**.

## 💡 Our Approach

LunaBot combines:

* ROS 2-based modular architecture
* Autonomous navigation and obstacle avoidance
* Habitat environmental monitoring
* Risk-aware mission prioritization
* Camera-based monitoring
* Operator dashboard and controls
* Simulated lunar habitat testing

The central idea is simple:

```text id="nqhv8i"
MONITOR → EVALUATE RISK → PRIORITIZE → NAVIGATE → INSPECT → REPORT
```

## 🧠 Key Innovation — Risk-Aware Patrol

Traditional autonomous navigation primarily solves:

> **How should I reach my destination?**

LunaBot adds a mission-level question:

> **Which destination needs me first?**

Environmental readings such as temperature and oxygen level can be combined with habitat-zone importance to determine patrol priority.

This allows LunaBot to move toward **condition-driven autonomous patrol** rather than relying only on a fixed waypoint sequence.

## 🏗️ System Architecture

```text id="8h0sqx"
              ┌─────────────────────┐
              │   Operator UI       │
              └──────────┬──────────┘
                         │
                         ▼
              ┌─────────────────────┐
              │   Mission Manager   │
              │  Risk Prioritizer   │
              └──────────┬──────────┘
                         │
        ┌────────────────┼────────────────┐
        ▼                ▼                ▼
   Navigation       Habitat Monitor    Perception
        │                │                │
        └────────────────┼────────────────┘
                         ▼
                      ROS 2
                         │
                         ▼
               Robot / Simulation
```

Detailed architecture: `docs/architecture.md`

## 🌡️ Habitat Monitoring

The prototype architecture considers environmental parameters such as:

* Temperature
* Oxygen level
* Habitat-zone status
* Zone criticality

Abnormal conditions can be used by the mission layer to influence patrol priority and alerts.

## 🤖 Technology Stack

* **ROS 2**
* **Python**
* **Gazebo / robotic simulation**
* **ROS 2 Navigation concepts**
* **Camera / perception pipeline**
* **Git & GitHub**

Additional technologies may be integrated as the prototype evolves.

## 📂 Repository Structure

```text id="nvkryx"
LunaBot/
│
├── README.md
├── LICENSE
├── .gitignore
│
├── lunabot_core/          # Working ROS 2 package
│
├── docs/
│   ├── architecture.md
│   ├── innovation.md
│   └── roadmap.md
│
└── media/
    ├── screenshots/
    └── demo/
```

## 🔄 Mission Workflow

```text id="yksgw1"
Sensor / Habitat Data
          ↓
Environmental Monitoring
          ↓
Risk Evaluation
          ↓
Priority Target Selection
          ↓
Autonomous Navigation
          ↓
Inspection
          ↓
Dashboard / Alert
          ↓
Continue Patrol
```

## 🌕 Why LunaBot?

Lunar exploration is not only about reaching the Moon — sustained exploration requires habitats that can be continuously monitored and maintained.

LunaBot explores how autonomous robotics can reduce routine astronaut workload by combining **mobility, habitat awareness and mission-level decision making** in a single ROS 2 architecture.

## 🛣️ Development

See:

* `docs/innovation.md` — Risk-aware patrol concept
* `docs/architecture.md` — System architecture
* `docs/roadmap.md` — Development roadmap

## 👥 Team

Developed as a four-member hackathon project with responsibilities distributed across:

* Project leadership, research and system design
* ROS 2 software and frontend development
* Hardware and electronics
* Integration, testing and support

## 🎯 Project Goal

Our goal is to demonstrate a prototype in which an autonomous robot can monitor a simulated lunar habitat, identify areas requiring attention, navigate safely toward mission targets and communicate its status to human operators.

---

**LunaBot — Autonomous eyes and wheels for the habitats beyond Earth. 🌙**

