# AGENTS.md

## Purpose

This document provides guidance for AI coding agents and contributors working on the OnIt-Robotics repository.

OnIt-Robotics is a lightweight ROS 2-native framework for capability-oriented agentic robotics.

The project focuses on embodied AI systems that can dynamically compose and execute capabilities such as perception, navigation, reasoning, manipulation, memory, safety, and model integration through natural language interaction and ROS 2-native tooling.

---

# Core Philosophy

OnIt-Robotics follows the philosophy of:

## Capability-Oriented Agentic Robotics

Robots should not be limited to a fixed set of tools or models.

Instead, robots should:
- determine what capabilities are required for a task
- dynamically bind models and tools
- safely execute actions through ROS 2
- remain modular and extensible

Natural language is not only used to command the robot.

Natural language is also used to:
- identify required capabilities
- compose execution pipelines
- select suitable models/providers
- extend robot functionality

---

# Core Principles

- ROS 2 native
- Lightweight and deployable
- Minimal dependencies
- Simulator-first development
- Safety-first execution
- Explicit and inspectable tool execution
- Model-agnostic integration
- Capability-oriented architecture
- Edge-device friendly
- Extensible to new robots and capabilities

---

# Dependency Philosophy

Keep dependencies minimal.

Avoid introducing large or unnecessary frameworks unless clearly justified.

Prefer:
- standard Python libraries
- lightweight abstractions
- ROS 2-native tooling
- modular optional dependencies

Heavy dependencies such as:
- large ML frameworks
- web frameworks
- GPU libraries
- experimental orchestration frameworks

should remain optional whenever possible.

---

# Safety Rules

Safety is a core requirement.

All motion-related commands must pass through safety validation layers.

Never allow direct unsafe motion execution without:
- obstacle awareness
- stop capability
- bounded motion constraints
- watchdog or timeout handling

Robotics safety is prioritized over agent autonomy.

---

# Architecture Direction

The repository should evolve toward a modular layered architecture:

```text
Core Agent Runtime
    ↓
Capability Registry
    ↓
ROS 2 Interface Layer
    ↓
Robot Profiles
    ↓
Simulation Layer
    ↓
Dynamic Capability Creation
```

Avoid tightly coupling:
- robot hardware
- model providers
- simulators
- capability definitions

---

# Capability System

Capabilities are first-class abstractions.

Examples:
- navigation
- scene understanding
- segmentation
- localization
- manipulation
- memory
- model training

Capabilities should:
- define inputs and outputs
- expose required ROS interfaces
- remain provider-agnostic when possible

Models are providers of capabilities.

The framework should support:
- swapping providers
- multiple providers per capability
- dynamic capability registration

---

# Simulation Philosophy

Simulation support is a core feature.

The framework should support:
- turtlesim
- lightweight simulators
- web-based simulators
- ROS-native simulation environments

Simulation should be usable without physical hardware.

---

# Coding Guidelines

Prefer:
- simple abstractions
- readable code
- explicit execution paths
- modular components
- type hints when practical

Avoid:
- deeply nested abstractions
- unnecessary metaprogramming
- hidden side effects
- overengineering

Keep robotics workflows understandable and debuggable.

---

# Initial MVP Goals

The initial MVP should focus on:

```text
Natural language
    ↓
Capability selection
    ↓
ROS 2 execution
```

Initial targets:
- turtlesim
- TurtleBot3
- simple motion tools
- basic perception/state tools
- safety-gated execution

---

# Long-Term Vision

The long-term goal is a lightweight robotics runtime where robots can:
- understand natural language goals
- determine required capabilities
- dynamically compose models and tools
- execute safely through ROS 2
- operate on real robots and simulators
- extend themselves with new capabilities when needed

The project should remain focused on robotics and embodied AI systems rather than becoming a large general-purpose agent framework.
