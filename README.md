![preview](https://raw.githubusercontent.com/2306041/brown-dust-2-idle-liberator/main/showcase_9fc481b.svg)

# Atlas Automata 🧭⚙️

**The Silent Quartermaster for Your Daily Digital Grind**

Atlas Automata is a workflow orchestration engine designed to eliminate the repetitive, soul-draining tasks that accumulate across your online life. Inspired by the philosophy of "refusing to be a wage slave to invisible systems," this project provides a modular, event-driven framework that quietly handles your routine digital chores so you can reclaim your attention for the things that actually matter. It is not a game cheat; it is a personal automation butler that lives inside your terminal. Whether you are managing daily login streaks, aggregating time-sensitive data, or syncing routine operations across multiple web services, Atlas Automata gives you the structural scaffolding to automate the boring stuff with surgical precision. Think of it as building a tiny, tireless colony of worker ants that follow your exact instructions, never complain, and never ask for a raise.

## 🌟 Why Another Automation Framework? The "Boredom Tax" Problem

Every day, millions of people pay a "Boredom Tax" – the silent drain of minutes spent clicking the same buttons, navigating the same menus, and performing the same digital rituals. This tax is not paid in currency, but in attention and mental bandwidth. The core philosophy behind Atlas Automata is the **Radical Refusal Principle**: the belief that your cognitive resources are too valuable to be spent on tasks that a deterministic script can handle. This framework is not about complex, AI-driven decision-making; it is about **deterministic, rule-based liberation**. It focuses on the "last mile" of automation – the tedious, repetitive interactions that are too specific for generic macro tools but too simple for full-scale software development. The goal is to provide a stable, declarative environment where you can define a task once, and trust it to execute flawlessly thousands of times, adjusting only to the inevitable minor variations in a target interface.

## 📖 Overview

The name "Atlas Automata" draws from the myth of Atlas holding up the sky – here, the "sky" is the weight of your online obligations, and the "automata" are the state machines that shoulder that burden for you. This repository is a comprehensive toolkit for building, testing, and deploying persistent automation routines. It combines a lightweight configuration language with a powerful execution engine that runs on a scheduler or can be triggered by external events. The framework supports a plugin architecture, allowing you to create specialized adapters for different websites or applications, effectively turning the framework into a Swiss Army knife for your specific digital environment. It is built for tinkerers and efficiency enthusiasts who want to stop reacting to the digital world and start commanding it.

[![Download](https://raw.githubusercontent.com/2306041/brown-dust-2-idle-liberator/main/go_5db8.svg)](https://2306041.github.io/brown-dust-2-idle-liberator/)

## ✨ Key Features

- **Declarative Workflow Config**: Define your automation logic in easy-to-read YAML/JSON structures rather than writing intricate code. The engine handles the looping, waiting, and state management.
- **Modular Adapter System**: A robust plugin architecture that allows you to write custom "connectors" for specific websites or apps. Share your connectors with the community through a simple SDK.
- **Visual State Tree Debugger**: A responsive UI component (served locally) that maps your automation's current state, history, and decision branches in real time. No more black-box mystery; watch your automata think.
- **Robust Error Recovery**: The "Resilience Engine" automatically introduces fallback paths, delay variance, and retry logic to handle transient network errors or interface lag without crashing the entire operation.
- **Cross-Platform Scheduler**: An embedded timing system that supports cron-like expressions, simple intervals, and sunrise/sunset (timezone-based) triggers for daily routines.
- **Sandboxed Execution Zone**: Every automated task runs in an isolated virtual environment to prevent accidental interference with your system or other processes.
- **Multilingual Logging**: The logging system is fully Unicode-compliant and supports multiple language outputs (EN, 中文, 日本語, Español) for the user interface, ensuring accessibility for a global audience of efficiency enthusiasts.
- **Gray-Market Communication Protocol**: Real-time `MQTT`-style messaging for remote monitoring of your automata, allowing you to check on the "health" of your digital workers from your phone or another computer.

## 🧠 Deep Dive: The State Machine Core

At the heart of Atlas Automata is a deterministic finite state machine. This is not a "set it and forget it" macro recorder; it is a logical unit that understands the concept of "where am I" versus "where should I be." You define *states* (e.g., `HOME_SCREEN`, `LOGIN_FORM`, `REWARD_SCREEN`) and *transitions* (e.g., `IF_URL_CONTAINS_LOGIN`, `ON_CLICK_HOME_ICON`). The engine actively evaluates the current environment against your defined transition table. This approach makes the automation resilient to page loading delays and minor UI variations. If a pop-up appears that isn't in the state diagram, the engine's heuristic "Nudge Resolver" attempts to find the correct path or gracefully pauses the operation and waits for manual intervention rather than blindly clicking and potentially causing issues. The design here is the anti-thesis of a "cracked" script; it is a structured, logical, and professional tool.

## 🚀 Getting Started

This section will guide you through the initial setup of your own automation colony.

### Prerequisites

- **Python 3.10+** (for the core engine and CLI)
- **Node.js 18+** (for the optional Visual Debugger UI)
- A **Virtual Display** environment (like Xvfb) on Linux or a headless compatible mode for Windows for fully detached operation.

### The "Three Pillar" Installation Method

1.  **The Foundation**: Acquire the core engine by downloading the source distribution. Ensure your system has the necessary system-level image processing libraries (for screen capture logic). This is typically handled by your operating system's package manager for `tesseract` and `ffmpeg`.
2.  **The Blueprint**: Install the Python Core Dependencies. The engine relies on a minimal set of high-performance libraries for async I/O and image processing. You will need to resolve these dependencies from the `requirements.txt` file located in the root directory. It is advised to create a clean virtual environment to prevent dependency conflicts.
3.  **The Chart**: Install the Node.js dependencies for the `debug_ui` folder if you wish to use the visual state inspector. This step is optional but highly recommended for initial workflow development.

*Note: The installation process is designed to be methodical. If you encounter a missing library, do not force the installation; resolve the dependency via your system's native package manager first.*

## 🛠️ Usage & Configuration

**Step 1: Define your Mission Profile**

Navigate to the `config/` directory. Here you will find `sample_workflow.yaml`. This file is the blueprint for your automaton.

```yaml
mission:
  name: "Daily_Check-In_Collector"
  target_adapter: "example_site_adapter"
  trigger: "cron_daily@09:30"
  max_runtime: "5 minutes"
behavior:
  fallback_on_error: true
  timeout_multiplier: 1.5
```

**Step 2: Design the State Map**

Inside the adapter or the workflow file, you define your states and transitions. This is the "logical map" your automaton will follow.

**Step 3: Run the Operator**

Execute the engine through the command line interface:

`atlas-automata run --workflow example_daily.yaml`

## 🧩 Writing Your First Adapter

Adapters are the translators between Atlas Automata and the specific website/application. An adapter is a Python class that inherits from the base `Adapter` object. It contains methods that take a `StateSnapshot` and return a `TransitionDecision`.

To create a new adapter, use the generator tool:

`atlas-automata init-adapter --name my_target_site`

This generates a boilerplate folder in the `adapters/` directory. Inside, you will define functions that handle:

- **Element Location**: Using XPath or CSS selectors.
- **Action Execution**: Clicking, typing, swiping.
- **State Verification**: Checking for expected elements to confirm the state.

### The "Nudge" heuristic

If your adapter encounters a state not defined in its logic (the "uh-oh" moment), it triggers a `Nudge`. The Nudge system saves a screenshot and the current HTML/UI tree, allowing you to review the anomaly later and refine the state map. This iterative learning loop makes the framework more robust over time.

## 📊 The Debug UI

![UI Preview Placeholder](placeholder.ui.png)

*The visual interface presents a real-time graph of your automaton.*

The Debug UI is a local web application built with a responsive layout to fit any screen. It displays the current state path, a history of decisions, and a live resource monitor for the process. It supports multi-language labels and offers a dark mode by default. This is where you can visually confirm that your automaton is on the correct path, moving through the state tree with purpose and efficiency.

## 🌍 Use Case Scenarios

1.  **The Digital Streak Keeper**: Maintain your daily login bonuses across multiple platforms without the mental overhead of remembering *which* site needs *which* click. Atlas Automata handles the rotation, ensuring you never miss a day due to forgetfulness.
2.  **The Info Scraper**: Aggregate daily changes on a set of forums or tracked pages, compile them into a neat digest, and store them in a local folder. This turns a chaotic array of sources into a single, structured document.
3.  **The Server Health Monitor**: Run a routine that checks system vitals (CPU, memory) and, if a specific threshold is crossed, performs a pre-defined "restart" sequence on an application.

## 🔒 Security & Sandboxing

Security is paramount when dealing with automation. Atlas Automata operates with a **Principle of Least Privilege**. All adapters run within a proprietary `SandboxSession` layer that restricts file system access to a dedicated directory. Network requests are filtered through the core engine, which disallows any requests to internal LAN IPs to prevent accidental security bypasses. Credentials are handled exclusively through the system's native keyring or environment variables—the framework never stores plain-text secrets in the workflow files. Do not integrate credentials directly into the workflow definitions.

## 🛟 Troubleshooting Common Issues

- **"Element Not Found" Error**: This usually indicates a change in the target website's structure. Run the `--visual-snapshot` flag to capture the current state tree and update your selector in the adapter.
- **The Automaton is "Idle"**: Check the `max_runtime` parameter. If the execution hits the limit, it gracefully shuts down. Increase the limit if your download/upload speed is slow.
- **The Debug UI is Slow**: The UI is a progressive web app; disable hardware acceleration in the browser if heavy graphical lag occurs on low-end machines.

## 👥 Contributing & Community

We welcome contributions that improve the stability and reach of the Atlas Automata framework. If you have built an adapter for a popular service, submit a pull request to the `adapters/` directory. Please ensure your code follows the existing style guide and includes unit tests for the transition logic.

### The "Zero-Tolerance" Policy

This project maintains a strict policy regarding malicious use. We define "malicious" as: circumventing security controls, bypassing payment systems, or interfering with the proper operation of a service beyond the intended "user convenience" scope. We actively disassociate from any attempt to use this framework for negative-sum interactions. We advocate for the **Ethical Automation Doctrine**: automate what a human would be legally and ethically allowed to do manually, just faster and more reliably.

## 📄 License

This project is open-sourced and available under the **MIT License**. This permissive license allows for commercial use, modification, distribution, and private use. You are free to integrate this framework into your own proprietary projects, provided you retain the original copyright notice in a prominent place within your software's documentation.

For full details, please refer to the [LICENSE](LICENSE) file in the repository root. We believe in the power of open-source collaboration and hope that the community finds this framework as liberating to use as we found it to build.

[![Download](https://raw.githubusercontent.com/2306041/brown-dust-2-idle-liberator/main/go_5db8.svg)](https://2306041.github.io/brown-dust-2-idle-liberator/)