# OnIt-Robotics

A lightweight ROS 2-native framework for capability-oriented agentic robotics.

---

## Overview

OnIt-Robotics is a robotics-focused fork and reimagining of the original OnIt framework developed by Dr. Rowel Atienza at the University of the Philippines.

While the original OnIt explores general-purpose agentic systems, OnIt-Robotics focuses specifically on embodied AI systems for ROS 2 robots, simulators, and robotics research.

The goal is to make agentic robotics easier to install, configure, extend, and deploy on real robots such as TurtleBot3, Clearpath Ridgeback, Franka Emika Arm, and other ROS-based platforms.

---

## Philosophy

OnIt-Robotics is built around the idea of **Capability-Oriented Agentic Robotics**.

A robot should not be limited to a fixed set of models, tools, or behaviors. Instead, it should be able to reason about the capabilities required for a task and dynamically compose perception, reasoning, planning, navigation, manipulation, memory, and safety modules.

In this framework, natural language is not only used to command the robot. It is also used to help the robot determine what capabilities it needs.

For example:

```text
User: Find the chair and move closer to it.

Required capabilities:
- scene understanding
- object localization
- safe motion
- obstacle awareness
```

Another example:

```text
User: The robot needs to detect rice panicles.

Required capabilities:
- object detection or segmentation
- dataset preparation
- model training
- model registration as a new capability
```

---

## Core Principles

- ROS 2 native
- Lightweight and deployable
- Simulator-first development
- Safety-first execution
- Capability-oriented architecture
- Model-agnostic integration
- Explicit and inspectable tool execution
- Edge-device friendly
- Minimal dependencies
- Extensible to new robots, models, and capabilities

---

## Planned Capabilities

OnIt-Robotics aims to support modular capabilities such as:

- Natural language robot control
- ROS 2 topic, service, and action tools
- TurtleBot3 support
- Clearpath Ridgeback support
- Manipulator support
- Turtlesim integration
- Web-based robot simulator
- VLM-based scene understanding
- Object detection and segmentation
- Navigation and SLAM integration
- Safety watchdogs and motion constraints
- Capability registry
- Model/provider swapping
- Dynamic capability creation
- Robot memory and task logging

---

## Initial MVP

The first milestone is intentionally small:

```text
Natural language → capability selection → ROS 2 execution
```

The initial target is to demonstrate this loop using:

- turtlesim
- TurtleBot3
- basic motion tools
- simple perception or state-reading tools
- safety-gated execution

---

## Long-Term Vision

The long-term vision is for OnIt-Robotics to become a lightweight runtime where robots can:

- understand natural language goals
- identify required capabilities
- select suitable models and tools
- execute actions through ROS 2
- operate safely on real hardware
- use simulators for testing
- create or register new capabilities when needed

Rather than being a large general-purpose agent framework, OnIt-Robotics aims to be a focused robotics runtime:

```text
Natural language in, safe ROS 2 capability execution out.
```

---

## Status

This project is in early research and development.

The repository is currently being redesigned from the original OnIt framework into a robotics-first architecture.

---

## Origins

OnIt-Robotics is based on the original OnIt framework by Dr. Rowel Atienza.

This fork explores a specialized direction focused on ROS 2, embodied AI, robotics simulation, perception, navigation, and safe robot execution.

---

## License

License information will follow the original OnIt repository unless changed later.
