# CAPABILITIES.md

# OnIt-Robotics Capability System

This document describes the capability system of OnIt-Robotics.

The capability system is one of the core architectural concepts of the framework.

---

# Philosophy

OnIt-Robotics follows the philosophy of:

## Capability-Oriented Agentic Robotics

Robots should not be limited to:
- fixed models
- fixed tools
- fixed pipelines
- fixed robot behaviors

Instead, robots should:
- determine required capabilities
- dynamically select providers
- compose execution pipelines
- extend functionality when necessary

In this framework:
- capabilities are first-class abstractions
- models are providers of capabilities
- robots consume capabilities to accomplish tasks

---

# What is a Capability?

A capability is a modular unit of robot functionality.

Examples:
- navigation
- object localization
- segmentation
- scene understanding
- manipulation
- memory
- localization
- SLAM
- model training

Capabilities define:
- inputs
- outputs
- requirements
- providers
- execution constraints
- ROS dependencies

---

# Capability Abstraction

A capability should describe:
- what functionality is provided
- not how it is internally implemented

Example:

```text
Capability:
object_segmentation
```

Possible providers:
- YOLO segmentation
- SAM
- Grounded-SAM
- future segmentation models

The higher-level agent runtime should not depend on a specific provider implementation.

---

# Capability Structure

Example conceptual structure:

```yaml
capability:
  name: object_segmentation
  type: perception

  description:
    Segment objects from an image.

  inputs:
    - image
    - text_prompt

  outputs:
    - masks
    - labels
    - confidence_scores

  providers:
    - yolo_seg
    - sam
    - grounded_sam

  required_topics:
    - /camera/image_raw/compressed

  safety_level: low
```

---

# Capability Categories

The capability system may eventually include categories such as:

## Perception

Examples:
- scene understanding
- object detection
- segmentation
- OCR
- pose estimation
- depth estimation

---

## Navigation

Examples:
- waypoint navigation
- obstacle avoidance
- path planning
- localization
- SLAM

---

## Manipulation

Examples:
- grasp planning
- pick-and-place
- arm motion
- object interaction

---

## Memory

Examples:
- semantic memory
- visited locations
- map annotations
- task history

---

## Safety

Examples:
- watchdogs
- obstacle checks
- emergency stop
- motion constraints
- timeout monitoring

---

## Communication

Examples:
- speech output
- speech recognition
- UI interaction
- remote monitoring

---

## Learning and Training

Examples:
- dataset preparation
- model training
- fine-tuning
- capability generation
- automatic evaluation

---

# Providers

Providers are implementations of capabilities.

Examples:

```text
Capability:
scene_understanding

Providers:
- Qwen-VL
- GPT-4o
- local VLM
```

Another example:

```text
Capability:
navigation

Providers:
- Nav2
- reactive navigation
- custom planner
```

The framework should support:
- provider swapping
- multiple providers
- provider fallback
- local and remote providers

---

# Capability Binding

Capability binding is the process of selecting providers for a task.

Example:

```text
User:
Find the chair and move closer.
```

Possible reasoning:

```text
Required capabilities:
- scene understanding
- object localization
- navigation
- safe motion
```

Possible provider binding:

```text
scene_understanding → Qwen-VL
object_localization → YOLO
navigation → Nav2
safe_motion → safety watchdog
```

The binding process should remain:
- modular
- inspectable
- overridable
- debuggable

---

# Dynamic Capability Registration

The framework should support dynamic registration of capabilities.

Examples:
- adding a new perception model
- adding a new robot profile
- registering a custom ROS tool
- registering a newly trained model

The system should avoid hardcoded capability assumptions whenever possible.

---

# Dynamic Capability Creation

A long-term goal of OnIt-Robotics is dynamic capability creation.

Example:

```text
User:
The robot needs to detect rice panicles.
```

Possible future behavior:

1. identify missing capability
2. determine required model type
3. prepare dataset pipeline
4. train model
5. validate model
6. register model as a capability provider

This direction is a future research goal.

---

# Capability Safety Levels

Capabilities may eventually include safety classifications.

Example:

```text
low:
- scene understanding
- OCR

medium:
- navigation planning
- localization

high:
- robot motion
- manipulator control
```

Higher-risk capabilities should require:
- additional validation
- safety checks
- execution constraints
- watchdog supervision

---

# Capability Composition

Complex robot tasks may require multiple capabilities working together.

Example:

```text
Task:
Pick up the red object.
```

Possible capability composition:

```text
- scene understanding
- object localization
- segmentation
- grasp planning
- manipulator control
- safety monitoring
```

The framework should support:
- modular composition
- reusable pipelines
- dynamic execution graphs

---

# Simulator Support

Capabilities should work in:
- simulators
- real robots
- hybrid environments

Simulation should be treated as a first-class execution environment.

---

# Initial MVP Capabilities

The initial MVP should remain intentionally small.

Initial capabilities may include:
- move_forward
- rotate
- stop
- read_robot_state
- read_pose
- basic scene description
- obstacle awareness

Initial targets:
- turtlesim
- TurtleBot3

---

# Long-Term Vision

The long-term vision of the capability system is a robotics runtime where robots can:
- reason about required functionality
- dynamically select providers
- compose capabilities safely
- operate across robots and simulators
- extend themselves with new capabilities

The system should remain:
- lightweight
- modular
- ROS-native
- safety-oriented
- practical for real robotics systems
