# Prometheus: Add README for task-template

## Project Overview

A template for creating Koii Tasks, providing a standardized framework for developing decentralized applications that run on the Koii network. This template enables developers to create blockchain-based tasks with a structured approach to task execution, submission, and distribution.

### Key Features

- Comprehensive task node structure with predefined function hooks
- Supports periodic task execution across a distributed network
- Flexible task logic implementation
- Built-in mechanisms for:
  - Task submission
  - Work validation
  - Reward distribution
  - Auditing

### Core Functionality

The template provides a scalable framework for creating decentralized tasks that run on the Koii network. It enables developers to define custom task logic while leveraging a standardized execution model that includes:

- Automated round-based task management
- IPFS data storage integration
- K2 settlement layer interactions
- Consensus-driven task validation
- Customizable reward distribution mechanisms

### Benefits

- Simplifies blockchain task development
- Provides a consistent architecture for decentralized applications
- Supports modular task design
- Enables developers to focus on core task logic
- Handles complex distributed computing challenges out of the box

## Getting Started, Installation, and Setup

### Prerequisites

Before you begin, ensure you have the following installed:
- Node.js (version 16.0.0 or higher)
- Docker Compose
- Yarn package manager

### Quick Start

1. Clone the repository:
```bash
git clone <repository-url>
cd k2-task-template
```

2. Install dependencies:
```bash
yarn install
```

### Development Setup

#### Local Development

1. Copy your Koii wallet key to the `config` folder as `id.json`

2. Configure environment variables:
Edit the `.env-local` file and set your task-specific environment variables. You can set two runtime options:
- `GLOBAL_TIMERS="true"`: Uses calculated average time slots
- `GLOBAL_TIMERS="false"`: Allows manual K2 calls with disabled round management

3. Build the project:
```bash
yarn webpack
```

#### Running Locally with Docker

1. Add your Task ID to the `.env-local` file in the `TASKS` environment variable

2. Start the local task node:
```bash
docker compose up
```

### Build for Production

To create a production-ready bundle:
```bash
yarn webpack
```

### Deployment

To deploy your task to the K2 testnet:
```bash
npx @_koii/create-task-cli
```

#### API Access

Your task's APIs will be available at:
- Base URL: `http://localhost:8080/task/{TASKID}`
- Task State: `http://localhost:8080/task/{TASKID}/taskState`

### Useful Commands

- Build project: `yarn webpack`
- Run tests: `yarn test` (if applicable)
- Deploy task: `npx @_koii/create-task-cli`

### Notes

- Ensure you have a [web3.storage](https://web3.storage) API key for IPFS storage
- Recommended to write unit tests for core logic functions
- Restart the task node after code modifications to apply changes