# Prometheus: Add README for task-template

## Project Overview

This is a comprehensive task node template for building and deploying decentralized applications on the Koii network. It provides developers with a robust framework for creating blockchain-powered tasks that can run across a distributed network of nodes.

### Purpose
The template enables developers to create and deploy tasks that can:
- Execute periodic work across a decentralized network
- Submit and validate task results
- Manage distribution of rewards
- Operate with consensus mechanisms

### Key Features
- Flexible task logic implementation
- Automatic and manual round management
- Built-in submission and distribution validation
- Support for multiple storage backends (IPFS, Arweave)
- Docker-based local development environment
- Seamless integration with Koii's K2 settlement layer

### Benefits
- Simplified task development process
- Standardized interfaces for network interactions
- Modular architecture for easy customization
- Built-in consensus and validation mechanisms
- Cross-platform compatibility
- Low-overhead deployment using Docker

## Getting Started, Installation, and Setup

### Prerequisites

Before getting started, ensure you have the following installed:
- Node.js (version >=16.0.0)
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

#### Local Development

To run the project in development mode:

1. Configure environment variables in `.env-local`:
   - Set `GLOBAL_TIMERS` to either `"true"` or `"false"`
   - Add any required custom environment variables

2. Start the development environment:
```bash
docker compose up
```

#### Building the Project

To build the task for deployment:
```bash
yarn webpack
# This creates a bundled executable for task deployment
```

### Deployment Preparation

1. Obtain a Web3.Storage API key from [web3.storage](https://web3.storage)
2. Prepare a Koii wallet:
   - Generate a new wallet using Koii CLI: `koii wallet create`
   - Or use an existing wallet by obtaining its keypair path

### Deploying to K2 Testnet

Deploy your task using the Koii Task CLI:
```bash
npx @_koii/create-task-cli
```
- Choose `DEVELOPMENT` deployment type
- Enter `main` when prompted for the deployment target

### Accessing Local APIs

After deployment, your task's APIs will be available at:
- Base URL: `http://localhost:8080/task/{TASKID}`
- Task State: `http://localhost:8080/task/{TASKID}/taskState`

### Important Notes

- Always test individual core logic functions with unit tests
- Restart the task node after code modifications
- Refer to the Koii documentation for detailed task development guidelines