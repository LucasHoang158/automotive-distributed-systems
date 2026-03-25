# Automotive Distributed Systems (QNX Camera-Oriented Experiments)

## Overview

This repository is a collection of experiments related to building an automotive application on QNX.

The main target is a **camera-like system**.  
Each topic in this repo explores one aspect of the system, such as:
- communication
- process separation
- rendering
- data flow

These parts are not fully integrated yet.  
They are small steps toward a larger system.

## Motivation

Modern automotive systems are becoming more complex.  
Applications like camera or ADAS are no longer a single process.

They involve:
- multiple modules
- data pipelines
- communication between components

On QNX, this often means:
- multi-process design
- strict performance constraints

This repo is used to explore these ideas in a simple and controlled way.

## Structure

Each folder represents one idea or experiment.

Examples:
- communication using vsomeip
- simple service interaction
- process-level separation
- basic pipeline behavior

They are loosely connected.  
All of them move toward the same goal: a camera system.

## System Direction

The target system can be seen like this:
Camera Input → Processing → Rendering → Output


Each stage may run in a separate process.

Communication between stages is done using middleware (e.g. vsomeip).

## Technologies

- C++
- QNX (target environment)
- vsomeip (for communication)
- EGL (for rendering, in some parts)
