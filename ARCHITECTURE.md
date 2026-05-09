# ARCHITECTURE.md

# OnIt-Robotics Architecture

This document describes the high-level architecture direction of OnIt-Robotics.

The architecture is intentionally modular, lightweight, ROS 2-native, and capability-oriented.

The goal is to create a robotics runtime that can dynamically compose perception, reasoning, navigation, manipulation, memory, safety, and model capabilities through natural language interaction and ROS 2-native tooling.

---

# Core Philosophy

OnIt-Robotics follows the philosophy of:

## Capability-Oriented Agentic Robotics

The framework should allow robots to:
- understand goals
- determine required capabilities
- select suitable providers
- safely execute through ROS 2
- dynamically extend functionality

Capabilities are first-class abstractions.

Models are providers of capabilities.

---

# High-Level System Architecture

```text
Natural Language Interface
            ↓
Agent Runtime
            ↓
Capability Planner
            ↓
Capability Registry
            ↓
Provider Binding Layer
            ↓
Safety Layer
            ↓
ROS 2 Interface Layer
            ↓
Robot or Simulator
```

---

# Architectural Layers

## 1. Natural Language Interface

Responsible for:
- receiving user instructions
- conversational interaction
- high-level task requests

Examples:
- CLI
- web UI
- chat interface
- future voice interface

Example input:

```text
Find the chair and move closer to it.
```

---

## 2. Agent Runtime

The central orchestration layer.

Responsible for:
- task execution flow
- capability requests
- execution state
- logging
- replanning
- coordination between modules

The runtime should remain:
- lightweight
- inspectable
- deterministic when possible

The runtime should avoid:
- hidden execution chains
- unnecessary abstraction layers
- tightly coupled logic

---

## 3. Capability Planner

Responsible for:
- determining required capabilities
- decomposing tasks
- identifying missing functionality
- selecting execution paths

Example:

```text
Task:
Find the chair and move closer.

Required capabilities:
- scene understanding
- object localization
- navigation
- safe motion
```

The planner should not assume:
- fixed models
- fixed providers
- fixed robot hardware

---

# 4. Capability Registry

The capability registry is a core abstraction of OnIt-Robotics.

Capabilities describe:
- inputs
- outputs
- requirements
- providers
- ROS dependencies
- safety level

Example:

```yaml
capability:
  name: object_segmentation
  type: perception
  inputs:
    - image
    - text_prompt
  outputs:
    - masks
    - labels
  providers:
    - yolo_seg
    - sam
```

The registry should support:
- dynamic registration
- multiple providers
- provider swapping
- capability discovery

---

# 5. Provider Binding Layer

Responsible for:
- connecting capabilities to providers
- selecting suitable models/tools
- abstracting provider-specific details

Providers may include:
- LLMs
- VLMs
- VLAs
- ROS nodes
- navigation stacks
- segmentation models
- external services

Examples:

```text
Capability:
scene_understanding

Possible providers:
- Qwen-VL
- GPT-4o
- local VLM
```

The framework should remain:
- provider-agnostic
- modular
- extensible

---

# 6. Safety Layer

Safety is mandatory.

All robot actions must pass through safety validation.

Responsibilities:
- motion constraints
- obstacle awareness
- watchdogs
- emergency stop
- timeout handling
- execution limits

The framework must prioritize:
- hardware safety
- human safety
- predictable execution

over:
- unrestricted agent autonomy

---

# 7. ROS 2 Interface Layer

Responsible for:
- ROS 2 communication
- topic publishing/subscribing
- services
- actions
- parameter interaction
- robot abstraction

This layer should abstract:
- robot-specific implementations
- ROS topic details
- hardware-specific differences

The framework should remain:
- ROS 2-native
- modular
- robot-agnostic where practical

---

# 8. Robot and Simulator Layer

The lowest layer represents:
- physical robots
- simulators
- hybrid simulation systems

Supported targets may include:
- turtlesim
- TurtleBot3
- Clearpath Ridgeback
- Franka Emika
- web-based simulators
- future ROS robots

Simulation is considered a first-class feature.

---

# Repository Direction

The repository should gradually evolve toward a modular structure similar to:

```text
onit_robotics/
├── core/
├── runtime/
├── capabilities/
├── providers/
├── ros/
├── robots/
├── safety/
├── simulators/
├── perception/
├── navigation/
├── memory/
└── cli/
```

This structure may evolve over time.

---

# Capability-Oriented Design

Traditional robotics systems often tightly bind:
- robot logic
- perception systems
- model implementations
- navigation pipelines

OnIt-Robotics instead treats:
- capabilities
- providers
- robots
- simulators

as loosely coupled components.

This allows:
- model swapping
- robot portability
- simulator portability
- dynamic capability composition
- future capability creation

---

# Dynamic Capability Creation

A long-term architectural goal is dynamic capability creation.

Example:

```text
User:
The robot needs to detect rice panicles.
```

Possible future behavior:

1. detect missing capability
2. identify required perception pipeline
3. prepare training workflow
4. train a model
5. register the model as a new capability

This functionality is a future research direction and not part of the initial MVP.

---

# Initial MVP Architecture

The initial MVP intentionally keeps the architecture small.

```text
Natural Language
    ↓
Simple Capability Selection
    ↓
ROS 2 Tool Execution
    ↓
Simulator or TurtleBot3
```

Initial MVP targets:
- turtlesim
- TurtleBot3
- simple motion tools
- basic state/perception tools
- safety-gated execution

---

# Long-Term Vision

The long-term goal is a lightweight robotics runtime where robots can:
- understand natural language goals
- determine required capabilities
- compose models and tools dynamically
- operate safely on real hardware
- use simulation for development
- extend themselves with new capabilities

The framework should remain:
- lightweight
- modular
- ROS-native
- practical for real robotics systems
- focused on embodied AI
