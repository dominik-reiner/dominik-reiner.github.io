---
title: "Can an AI Agent Take Care of Your Plant? Introducing Agent Basil"
date: 2025-12-23T02:00:00+01:00
draft: true
tags: ["ai-agents", "langraph", "mcp", "gemini", "iot", "esp32", "automation"]
summary: "I built Agent Basil, an AI agent that autonomously cares for a basil plant using vision, sensors, and physical actuators. Here's how it combines visual assessment with sensor data to make intelligent decisions."
---

**TL;DR**: I built Agent Basil, an AI agent that uses a camera and sensors to autonomously care for a basil plant because, apparently, I can't. Using an LLM, the agent assesses the plant's health from an image, gathers data from sensors, and decides on the best course of action—like watering the plant or telling me what to do. The results were surprising: the agent successfully recovered from its own overwatering mistake to nurse a dying plant back to health.

---

Most of us have heard about AI agents automating tasks like sorting emails or making a reservation. But what about automating **physical tasks**?

I wanted to try it out and created **Agent Basil**. Why basil? Well, because those store-bought basil plants always seem to die, and I figured a smart AI would have a better chance of keeping it alive than me.

![Agent Basil Setup](/images/agent-basil/agent_basil_setup.jpg)
*The full hardware setup: ESP32-CAM, sensors, and the water pump.*

Agent Basil consists of a camera, some sensors, and a water pump—all made available to the agent via MCP. Agent Basil makes a visual investigation of the plant and is free to fetch sensor data, water the plant, or give me a task to help it thrive.

## How Agent Basil Works

Agent Basil is an experimental AI agent designed to autonomously care for a basil plant. It goes beyond simple data processing; it's a system that can **perceive, diagnose, and physically intervene** to achieve a desired real-world outcome.

Its core functionality is built on a few key components:

- **LangGraph**-powered state machine to orchestrate the agent and context.
- **FastMCP** as a critical go-between, dynamically creating tools that connect the agent to local hardware.
- **Google Gemini** as the LLM, interpreting the plant's condition from images and choosing the next action.

![Agent Basil Camera View](/images/agent-basil/agent_basil_closeup.jpg)

The agent's operational cycle is a continuous loop of assessment and action. It starts with a visual input from an **ESP32-CAM**, which captures an image of the plant. This image is then sent to the LLM. I specifically instructed the agent to adopt a "casual, humorous, and maybe a little sassy" persona to make the logs more engaging. Based on the visual input, it generates a hypothesis—for example, *"The leaves are drooping, so the soil might be dry."*

To confirm this, the agent investigates further, using its tools to collect environmental data from sensors connected to an **ESP8266**, checking soil moisture, temperature, and humidity. Based on a confident diagnosis, the agent decides on the optimal action, whether that's activating the water pump or, if the problem is beyond its control (like a pest infestation), dispatching a specific task to me, its human caretaker. If no action is needed, the agent simply waits for its next turn.

## From "Desert" to "Small Victory": A Two-Week Case Study

To see if this actually worked, I let Agent Basil run wild from **September 1st to September 14th**.

### Sept 01: The Crisis
The agent woke up to a disaster. The plant was visually "super wilted" and the soil moisture was a critical **7.14%**.

![Basil in Crisis (Sept 01)](/images/agent-basil/basil_sad.jpg)
*Sept 01: The "desert-like" state that Agent Basil encountered.*

> **Agent's Internal Monologue:** "Yikes, that's practically desert-like! Triggering irrigation because, obviously, it needed water!"

### Sept 04: The Overcorrection
Fighting the latency of the physical world, the agent over-compensated. It watered the plant, didn't see the sensor move fast enough, and watered again. The result? **100% moisture**.
> **Agent's Internal Monologue:** "Whoops! A bit too much love, perhaps? The best thing we can do right now is absolutely nothing. It needs time for the roots to breathe."

### Sept 10: The Human Bottleneck
Even when the moisture levels were perfect, the plant still looked pale. The agent correctly deduced that it had reached the limits of its own tools and that the problem was now me.
> **Agent's Internal Monologue:** "I've poked the human about this before, but it seems our little friend is still waiting for its gourmet meal [fertilizer]. ... No further action needed for this turn, Basil out!"

### Sept 14: The Turnaround
After a week of careful "swamp management"—refusing to water despite the plant looking sad—the agent finally logged a win.

![Basil Recovering (Sept 14)](/images/agent-basil/basil_better.jpg)
*Sept 14: A visible recovery and a "small victory" for the agent.*

> **Agent's Internal Monologue:** "Looking a bit better in terms of wilting than in previous turns, which is a **small victory**! The immediate crisis of dehydration seems to be over."

### The Takeaway
This experiment illustrates the potential of applying AI agents to physical tasks. By giving the model the right tools — vision to see, sensors to feel, and actuators to act — we transformed a text-processing engine into a capable gardener. Agent Basil didn't just follow a script; it observed its environment and made autonomous decisions to keep the plant alive, proving that AI can successfully bridge the gap to the physical world given the right interface.

![Agent Basil Reasoning Example](/images/agent-basil/agent_basil_example.jpg)
*An example of the agent's multi-modal reasoning in action.*

---

If you're interested in exploring the code and documentation, they are available on my [GitHub](https://github.com/dominik-reiner/agent-basil).

