# ROADMAP.md

# OnIt-Robotics Roadmap

This document outlines the planned development roadmap for OnIt-Robotics.

The roadmap is intentionally incremental to keep the project lightweight, modular, and practical for real robotics systems.

The long-term vision is ambitious, but the project should evolve through small, testable milestones.

---

# Phase 0 — Foundation

Goal:
Establish the philosophy, architecture direction, and development workflow.

## Tasks

- [x] Fork original OnIt repository
- [x] Create project identity and philosophy
- [x] Create README.md
- [x] Create AGENTS.md
- [ ] Create ARCHITECTURE.md
- [ ] Create CAPABILITIES.md
- [ ] Clean repository structure
- [ ] Remove non-robotics dependencies
- [ ] Define lightweight package structure
- [ ] Setup Codex-assisted development workflow

---

# Phase 1 — Minimal ROS Agent Runtime

Goal:
Create the smallest possible end-to-end robotics agent loop.

## MVP Target

```text
Natural language
    ↓
Capability selection
    ↓
ROS 2 execution
```

## Initial Targets

- turtlesim
- TurtleBot3

## Tasks

- [ ] Minimal CLI
- [ ] ROS 2 interface layer
- [ ] Motion tool abstraction
- [ ] Safety-gated motion execution
- [ ] Basic capability registry
- [ ] Tool execution logging
- [ ] Minimal configuration system
- [ ] Simple natural language → tool execution loop

## Example Commands

```text
Move forward.
Rotate left.
Move in a square.
Stop.
```

---

# Phase 2 — Capability Registry System

Goal:
Formalize capabilities as first-class abstractions.

## Tasks

- [ ] Capability schema definition
- [ ] Capability metadata system
- [ ] Capability discovery
- [ ] Provider registration
- [ ] Multi-provider support
- [ ] Capability dependency resolution
- [ ] Runtime capability binding

## Example Capabilities

- motion
- scene understanding
- object localization
- segmentation
- navigation
- memory
- safety
- model training

---

# Phase 3 — Simulator Support

Goal:
Support simulator-first robotics development.

## Simulators

- turtlesim
- lightweight internal simulator
- web-based simulator
- optional Gazebo/Ignition integration

## Tasks

- [ ] Turtlesim profile
- [ ] Lightweight simulator API
- [ ] WebSocket simulator bridge
- [ ] Browser-based visualization
- [ ] Fake LiDAR support
- [ ] Fake camera support
- [ ] Simulated robot state
- [ ] Multi-world support

## Long-Term Goal

```text
A robotics runtime that can be developed and tested
without requiring physical hardware.
```

---

# Phase 4 — Real Robot Integration

Goal:
Support real ROS 2 robots with safe execution.

## Initial Robot Targets

- TurtleBot3
- Clearpath Ridgeback

## Future Robot Targets

- Franka Emika
- custom ROS robots
- manipulator systems
- mobile manipulators

## Tasks

- [ ] Robot profiles
- [ ] Topic/service/action adapters
- [ ] Camera interfaces
- [ ] LiDAR interfaces
- [ ] Odometry interfaces
- [ ] Safety watchdogs
- [ ] Motion limits
- [ ] Heartbeat monitoring
- [ ] Emergency stop integration

---

# Phase 5 — Dynamic Capability Binding

Goal:
Allow the robot to dynamically select suitable tools and models for a task.

## Example

```text
User: Find the chair.

Required capabilities:
- scene understanding
- object localization
- navigation
- safe motion
```

## Tasks

- [ ] Dynamic provider selection
- [ ] Model swapping
- [ ] VLM abstraction layer
- [ ] LLM abstraction layer
- [ ] Navigation capability binding
- [ ] Perception pipeline composition
- [ ] Capability planning

## Candidate Providers

- local VLMs
- cloud VLMs
- YOLO
- segmentation models
- SLAM/navigation stacks
- future VLAs

---

# Phase 6 — Dynamic Capability Creation

Goal:
Allow the robot to create or register new capabilities when required.

## Example

```text
User: The robot needs to detect rice panicles.
```

Possible system behavior:

- determine required perception capability
- identify missing capability
- prepare training pipeline
- train a model
- register model as a new capability

## Tasks

- [ ] Dataset pipeline support
- [ ] Training workflow abstraction
- [ ] Automatic capability registration
- [ ] Capability persistence
- [ ] Model lifecycle management
- [ ] Capability validation/testing

---

# Phase 7 — Advanced Systems

Goal:
Explore more advanced embodied AI systems.

## Possible Research Directions

- multi-robot coordination
- robot memory systems
- semantic mapping
- long-horizon planning
- embodied VLA systems
- multi-agent robotics
- cloud-edge hybrid robotics
- collaborative robot learning
- adaptive autonomy
- autonomous capability evolution

---

# Long-Term Vision

OnIt-Robotics aims to become a lightweight runtime for capability-oriented embodied AI systems.

The framework should allow robots to:

- understand natural language goals
- determine required capabilities
- compose models and tools dynamically
- execute safely through ROS 2
- operate in simulation and real hardware
- extend themselves with new capabilities when necessary

The project should remain:
- lightweight
- modular
- ROS-native
- safety-oriented
- practical for real robotics systems

rather than becoming a large general-purpose agent framework.
