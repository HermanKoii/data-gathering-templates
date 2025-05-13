# Prometheus: Add README for task-template

## Project Overview

This is a template for developing decentralized tasks on the Koii Network, providing a standardized framework for creating blockchain-based distributed computing applications. The template enables developers to build complex, consensus-driven tasks that can be executed across a network of nodes with built-in mechanisms for work submission, validation, and reward distribution.

#### Key Features
- Periodic round-based task execution
- Automated task node interactions
- Flexible task logic implementation
- Built-in consensus and validation mechanisms
- Support for IPFS data storage
- Seamless integration with the K2 settlement layer

#### Core Functionality
The template provides a structured approach to developing decentralized tasks, with predefined lifecycle functions that handle critical aspects of distributed computing:
- Automated task execution
- Submission of work results
- Generation and validation of distribution lists
- Auditing mechanisms for ensuring network integrity
- Configurable reward distribution strategies

Tasks built using this template can leverage the Koii Network's infrastructure to create scalable, trustless applications that run across multiple nodes while maintaining data integrity and providing economic incentives for participation.

## Getting Started, Installation, and Setup

### Prerequisites

Before you begin, ensure you have the following installed:
- Node.js (version 16.0.0 or higher)
- Docker Compose
- Yarn or npm package manager

### Installation

1. Clone the repository:
```bash
git clone https://github.com/your-repository/K2-Task-Template.git
cd K2-Task-Template
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

1. Configure environment variables:
   - Open `.env-local` file
   - Set necessary environment variables
   - Add your Task ID to the `TASKS` environment variable

2. Prepare your wallet:
   - Link or copy your Koii wallet as `config/id.json`

3. Run the project:
```bash
# Build the project
yarn webpack

# Start the local node
docker compose up
```

#### Runtime Options

The project supports two runtime modes:

1. Global Timers Enabled (`GLOBAL_TIMERS="true"`):
   - Automatically calculates average time slots
   - IPC calls are managed automatically

2. Manual Mode (`GLOBAL_TIMERS="false"`):
   - Allows manual calls to K2
   - Disables automatic round management
   - Transactions only accepted during specific periods

### Deployment

#### Build for Production

Prepare your task for deployment:
```bash
yarn webpack
```

#### Deploy to K2 Testnet

1. Use the Koii Task CLI:
```bash
npx @_koii/create-task-cli
```

2. Follow the CLI prompts:
   - Select deployment type (recommend DEVELOPMENT)
   - Enter `main` when prompted
   - Provide necessary wallet and configuration details

### Accessing APIs

After deployment, your task's APIs will be available at:
- Base URL: `http://localhost:8080/task/{TASKID}`
- Task State: `http://localhost:8080/task/{TASKID}/taskState`

### Important Notes

- Ensure you have a [web3.storage](https://web3.storage) API key for IPFS storage
- Create a Koii wallet for gas fees and bounty funding
- Write unit tests to verify core logic functions