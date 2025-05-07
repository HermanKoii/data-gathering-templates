# Prometheus: Add README for task-template

## Project Overview

K2-Task-Template is a comprehensive framework for developing and deploying decentralized tasks on the Koii network. It provides developers with a standardized template for creating blockchain-based applications that operate on a periodic, round-based consensus mechanism.

### Key Features
- Structured task development framework for Koii network applications
- Supports periodic task execution across distributed nodes
- Integrated IPFS data storage and K2 settlement layer interaction
- Flexible task logic implementation with predefined function hooks
- Support for both automated and manual task management

### Core Functionality
The template enables developers to create decentralized tasks that run in synchronized rounds across multiple nodes. Tasks can upload data to IPFS, post content identifiers (CIDs) to the K2 settlement layer, and communicate via REST APIs and WebSockets. 

### Benefits
- Simplifies blockchain task development
- Provides a consistent architecture for distributed computing
- Enables gradual consensus through structured round-based execution
- Supports flexible reward distribution and task validation mechanisms

## Getting Started, Installation, and Setup

### Prerequisites

Before getting started, ensure you have the following installed:
- Node.js (version 16.0.0 or higher)
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

3. Configure your environment:
- Copy `.env-local.example` to `.env-local` (if applicable)
- Update environment variables as needed

### Development Setup

#### Running in Development Mode

To run the application in development mode:

```bash
# Option 1: Global Timers Enabled (Automatic Synchronization)
GLOBAL_TIMERS=true yarn start

# Option 2: Manual Mode (Disabled Automatic Triggers)
GLOBAL_TIMERS=false yarn start
```

#### Building for Production

Prepare your task for deployment by creating a production bundle:

```bash
yarn webpack:prod
```

### Deployment Preparation

#### Wallet Setup
1. Generate a Koii wallet (if not already created):
```bash
npx @_koii/create-task-cli wallet create
```

2. Obtain a Web3.Storage API key from [web3.storage](https://web3.storage/)

#### Deploy to K2 Testnet
```bash
npx @_koii/create-task-cli
```

### Local Node Testing

1. Copy your wallet key to the `config` folder as `id.json`
2. Update `.env-local` with your Task ID
3. Start the local docker environment:
```bash
docker-compose up
```

### API Access

- Base API URL: `http://localhost:8080/task/{TASKID}`
- Task State Endpoint: `http://localhost:8080/task/{TASKID}/taskState`

### Important Notes

- Ensure all environment variables are correctly configured
- Restart the task node after code modifications
- Run `yarn webpack` to update the task bundle before restarting