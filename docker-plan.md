# Docker Module Design

Review each module in the Docker topic. For each module, make note of where the modules are lacking, and produce a bullet-pointed structure for how it should be constructed.

## Learning Objectives

Consider the learning objectives for each module. By the end of the module, the delegate should understand:

- when this technology is used 
- why this technology is used
- how to use this technology

## Design Philosophy

When thinking about your module structure, make sure it hits the following design points as best they can. These points apply more to the theory-based modules that introduce a new concept (e.g. volumes, images, containers) and less so to modules like Compose CLI or Dockerfile Instructions which just contain commands/syntax.

- Modules should contextualise the **why** of a particular part of Docker using a **scenario** or **problem**, then providing the solution
- Concepts should be explained **visually** (as well as textually) wherever appropriate - diagrams diagrams diagrams!!
- Exercises should give delegates more practical scenarios to employ what they've learnt in the theory

## General Structure

Below is a general structure for how the modules should be laid out. As with the design philosophy points, this applies more to the theory modules. This is not a strict structure, more a guideline.

- Overview
    - Introduces what the module is about in a broad high-level sense
    - Learning objectives here
- Use Case
    - Propose a scenario/issue/problem, e.g. how do I make sure my app runs the same across production environments?? (you could even relate it back to the CI pipeline!!)
    - Solution is the module topic, e.g. containers
- Technology
    - Introduces the technology and its features
    - List of benefits of this technology
- Further technical information
    - This would be where you talk about syntax etc.
- Tutorial
    - A guided tutorial of how to use a technology
- Exercise
    - An unguided exercise to allow them to apply what they have learnt
    - Provide stretch goals