# Prometheus: Add README for task-template

## Project Overview

K2-Task-Template is a flexible framework for developing decentralized computational tasks on the Koii network. It provides a robust, round-based system for executing distributed computing tasks with built-in mechanisms for submission, validation, and reward distribution.

### Core Purpose
The template enables developers to create scalable, consensus-driven tasks that can be run across a distributed network of nodes. It abstracts the complexities of decentralized task management, allowing focus on core task logic while providing a standardized execution environment.

### Key Features
- **Periodic Task Execution**: Tasks run in structured rounds with defined windows for work submission and auditing
- **Flexible Core Logic**: Customizable task, submission, and distribution logic through modular function interfaces
- **Consensus Mechanism**: Built-in validation and auditing processes to ensure task integrity
- **Reward Distribution**: Configurable reward systems for nodes participating in task execution
- **Multi-Environment Support**: Compatible with development, IPFS, and Arweave deployment modes

### Benefits
- Simplifies development of distributed computing tasks
- Provides a standardized framework for decentralized task execution
- Supports transparent and verifiable task submission and validation
- Enables dynamic reward mechanisms for task participants
- Reduces complexity of building peer-to-peer computational networks

## Getting Started, Installation, and Setup

### Prerequisites

Before getting started, ensure you have the following installed:
- Node.js (version >=16.0.0)
- Docker Compose
- Yarn package manager

### Quick Start

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd <repository-name>
   ```

2. Install dependencies:
   ```bash
   yarn install
   ```

### Development Mode

To run the task in development mode:

1. Configure environment variables in `.env-local`:
   - Set `GLOBAL_TIMERS` to either `"true"` or `"false"`
   - Add any required custom environment variables

2. Run the task:
   ```bash
   yarn start
   ```

### Building for Production

To build the task for deployment:

```bash
yarn webpack
```

This creates a bundled executable for the task node.

### Local Node Testing

1. Copy your Koii wallet key to the `config` folder as `id.json`

2. Update `.env-local` with your Task ID

3. Start the local task node:
   ```bash
   docker compose up
   ```

### API Access

- Base API URL: `http://localhost:8080/task/{TASKID}`
- Task State Endpoint: `http://localhost:8080/task/{TASKID}/taskState`

### Deployment

Deploy your task to the K2 testnet using the Koii Task CLI:
```bash
npx @_koii/create-task-cli
```

Follow the interactive prompts to complete the deployment process.

### Notes

- Ensure all dependencies are installed before running
- Refer to the project's core logic files (`index.js`, `NamespaceWrappers.js`, `coreLogic.js`) for task-specific implementations