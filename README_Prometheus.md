# Prometheus: Add README for task-template

## Project Overview

This is a template for developing decentralized tasks on the Koii Network, providing developers with a comprehensive framework for creating, deploying, and managing distributed computing tasks across a network of nodes.

The template enables developers to build blockchain-based applications that can run periodically across multiple nodes, with built-in consensus and reward mechanisms. Key features include:

### Task Execution Model
- Structured task execution using a round-based system
- Periodic task scheduling with defined time windows
- Automatic node participation and data synchronization

### Decentralized Workflow
- IPFS integration for distributed data storage
- K2 settlement layer for transaction management
- Support for REST APIs and WebSocket communication

### Flexible Task Development
- Customizable core logic implementation
- Modular functions for task, submission, validation, and distribution
- Support for manual and automated node interactions

### Network Compatibility
- Compatible with multiple blockchain networks
- Easy deployment using Koii's task creation CLI
- Local testing with Docker compose environment

The template simplifies the complex process of building decentralized applications by providing a robust, extensible framework for distributed computing tasks.

## Getting Started, Installation, and Setup

### Prerequisites

Before you begin, ensure you have the following installed:
- Node.js (version 16.0.0 or higher)
- Docker Compose
- Yarn or npm package manager

### Quick Start

1. Clone the repository:
```bash
git clone <repository-url>
cd <repository-name>
```

2. Install dependencies:
```bash
yarn install
# or
npm install
```

### Development Setup

#### Environment Configuration

1. Copy your K2 wallet:
   - Link or copy your wallet to the `config` folder as `id.json`

2. Configure environment variables:
   - Open `.env-local` 
   - Add your Task ID to the `TASKS` environment variable

#### Running the Project

You have two runtime options:

1. With Global Timers (Recommended for Development):
   - Set `GLOBAL_TIMERS="true"` in `.env-local`
   - This calculates average time slots for IPC calls

2. Without Global Timers:
   - Set `GLOBAL_TIMERS="false"` in `.env-local`
   - Enables manual calls to K2
   - Transactions are only accepted during specific periods

#### Local Development

To run the project locally:
```bash
docker compose up
```

#### Building for Production

To create a production bundle:
```bash
yarn webpack
# or
yarn webpack:prod
```

### Deployment

To deploy your task to the K2 testnet:
```bash
npx @_koii/create-task-cli
```

### Accessing APIs

- Base API URL: `http://localhost:8080/task/{TASKID}`
- Task State API: `http://localhost:8080/task/{TASKID}/taskState`

### Redeploying Changes

1. Rebuild the bundle:
```bash
yarn webpack
```

2. Restart the task node:
```bash
docker compose up
```

### Notes
- Ensure you have a [web3.storage](https://web3.storage) API key for IPFS storage
- Detailed task configuration can be found in `config-task.yml`