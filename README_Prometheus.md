# Prometheus: Add README for task-template

## Project Overview

This is a template for developing decentralized tasks on the Koii Network, providing a robust framework for creating, executing, and managing distributed computational tasks across a network of nodes.

### Core Purpose
The template enables developers to build scalable, consensus-driven applications that can run periodically across multiple nodes, with built-in mechanisms for task submission, validation, and reward distribution.

### Key Features
- Structured task execution in timed rounds
- Automated node coordination and synchronization
- Flexible task logic implementation
- Integrated IPFS and K2 settlement layer support
- Comprehensive lifecycle management for tasks
  - Task execution
  - Result submission
  - Validation
  - Auditing
  - Reward distribution

### Technical Advantages
- Modular architecture allowing easy customization
- Standardized interfaces for task node interactions
- Support for both automated and manual transaction management
- Built-in consensus mechanism for distributed computing
- Seamless integration with the Koii ecosystem

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

#### Configuration
1. Copy your Koii wallet key into the `config` folder as `id.json`
2. Open `.env-local` and configure environment variables as needed

#### Running the Project

##### Development Mode
To run the project in development mode:
```bash
# Option 1: With global timers enabled
GLOBAL_TIMERS=true npm start
# or
GLOBAL_TIMERS=true yarn start

# Option 2: With manual K2 calls
GLOBAL_TIMERS=false npm start
# or
GLOBAL_TIMERS=false yarn start
```

##### Local Docker Deployment
To run the task node locally using Docker:
```bash
# Add your TaskID to .env-local
docker-compose up
```

### Building for Production

Prepare your project for deployment:
```bash
# Build webpack bundle
yarn webpack
# or
npm run webpack
```

### Deployment

To deploy your task to the K2 testnet:
```bash
npx @_koii/create-task-cli
```

### Accessing APIs

Once running, your task's APIs will be available at:
- Base URL: `http://localhost:8080/task/{TASKID}`
- Task State: `http://localhost:8080/task/{TASKID}/taskState`

### Notes
- Replace `{TASKID}` with the task ID obtained during deployment
- Ensure you have a Web3.Storage API key for IPFS interactions
- Refer to the [Koii documentation](https://docs.koii.network) for detailed task development guidelines