# Prometheus: Add README for task-template

## Project Overview

K2-Task-Template is a comprehensive framework for developing and deploying decentralized computing tasks on the Koii Network. It provides developers with a robust template for creating distributed applications that can run across a network of nodes with built-in consensus mechanisms.

### Key Features

- **Periodic Task Execution**: Tasks run in structured rounds with defined time windows for execution, submission, and validation
- **Decentralized Infrastructure**: Leverages the K2 settlement layer for secure, transparent task management
- **Flexible Deployment**: Supports multiple deployment options including development, ARWEAVE, and IPFS networks
- **Comprehensive Task Lifecycle Management**: Includes built-in functions for task execution, submission, auditing, and reward distribution
- **Cross-Node Coordination**: Enables nodes to collaborate by uploading data to IPFS and posting results to the K2 settlement layer

### Core Capabilities

The template allows developers to create sophisticated distributed computing tasks with:
- Customizable task logic
- Automatic submission and validation processes
- Flexible reward distribution mechanisms
- Support for manual and automated transaction handling

Ideal for developers looking to build decentralized applications that require coordinated, consensual computation across a distributed network of nodes.

## Getting Started, Installation, and Setup

### Prerequisites

Before getting started, ensure you have the following installed:
- Node.js (version 16.0.0 or higher)
- Docker Compose
- Yarn package manager

### Quick Start

1. Clone the repository:
```bash
git clone https://github.com/your-repo/K2-Task-Template.git
cd K2-Task-Template
```

2. Install dependencies:
```bash
yarn install
```

### Development Setup

#### Environment Configuration

1. Copy your Koii wallet key:
   - If you don't have a wallet, create one using the [Koii CLI documentation](https://docs.koii.network/develop/koii-software-toolkit-sdk/using-the-cli#create-a-koii-wallet)
   - Copy your wallet keypair to `config/id.json`

2. Configure environment variables:
   - Open `.env-local`
   - Add your Task ID after deploying to K2
   - Set custom environment variables as needed

### Running the Project

#### Development Mode

You have two runtime options in the development environment:

1. With Global Timers (Recommended):
   - Set `GLOBAL_TIMERS="true"` in `.env-local`
   - Automatic IPC calls based on average time slots

2. Manual Calls Mode:
   - Set `GLOBAL_TIMERS="false"` in `.env-local`
   - Manual K2 transaction calls
   - Transactions only accepted during specific periods

#### Local Node Execution

Run the task node locally using Docker Compose:
```bash
docker compose up
```

### Build for Production

To create a deployable bundle:
```bash
yarn webpack
```

### Deployment

Deploy your task to the K2 Testnet:
```bash
npx @_koii/create-task-cli
```

### Accessing APIs

After local deployment, your task's APIs will be available at:
- Base URL: `http://localhost:8080/task/{TASKID}`
- Task State: `http://localhost:8080/task/{TASKID}/taskState`

### Redeploying Changes

1. Rebuild the bundle:
```bash
yarn webpack
```

2. Restart the task node:
```bash
docker compose up
```

### Troubleshooting

- Ensure all prerequisites are installed
- Verify wallet key and Task ID configuration
- Check Docker Compose logs for any deployment issues