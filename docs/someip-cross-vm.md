# SOME/IP-Based Communication Across Virtual Machines

## Overview

In virtualized automotive systems, multiple guest operating systems (e.g., RTOS and Linux) run on a shared SoC under a hypervisor. These guests are isolated and cannot communicate via direct function calls.

This guide describes how to establish inter-VM communication using SOME/IP over a virtual Ethernet interface.

## Architecture

- RTOS guest: service provider
- Linux/General-purpose guest: service consumer
- Transport: virtual Ethernet
- Middleware: SOME/IP + CommonAPI

## Key Concepts

### Services
Named interfaces exposing methods and events.

### Methods
Client-to-server request/response communication.

### Events
Server-to-client asynchronous notifications.

### Proxy / Stub
- Proxy: client-side interface
- Stub: server-side implementation

## Interface Definition Example

```fidl
interface IMediaService {
    version { major 1 minor 0 }

    method getStatus {
        out { Boolean isActive }
    }

    broadcast onServiceStateChanged {
        out { ServiceState state }
    }
}
