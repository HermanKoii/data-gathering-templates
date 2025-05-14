# Prometheus: Add README for task-template

## Project Overview

This is a Koii Task Template designed to help developers create and deploy decentralized tasks on the Koii network. The template provides a structured approach to building distributed computing applications that operate on a round-based consensus mechanism.

### Key Features
- Structured task development framework for Koii network applications
- Predefined function interfaces for core task logic
- Support for periodic task execution across distributed nodes
- Flexible task submission and validation mechanisms
- Built-in methods for:
  - Task execution
  - Submission management
  - Distribution list generation
  - Node validation
  - Auditing processes

### Core Capabilities
The template enables developers to create tasks that:
- Run on a round-based structure
- Upload data to IPFS
- Post Content Identifiers (CIDs) to the K2 settlement layer
- Communicate across REST APIs and WebSockets

### Benefits
- Simplifies development of decentralized computing tasks
- Provides a standardized approach to building distributed applications
- Offers comprehensive hooks for custom task logic
- Supports flexible deployment and testing workflows

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

### Development Setup

#### Local Development

To run the project in development mode:

1. Set up environment variables:
   - Copy `.env-local.example` to `.env-local`
   - Configure necessary environment variables

2. Run the project:
```bash
# For development with global timers
GLOBAL_TIMERS=true docker-compose up

# For manual mode without automatic triggers
GLOBAL_TIMERS=false docker-compose up
```

### Building for Production

Prepare your task for deployment:

1. Bundle the project:
```bash
yarn webpack
```

2. Deploy to K2 Testnet:
```bash
npx @_koii/create-task-cli
```

### Configuration Notes

- Modify `coreLogic.js` to implement task-specific logic
- Customize task functions like `_task()`, `_fetchSubmission()`, etc.
- Ensure proper implementation of task, submission, and distribution logic

### Accessing APIs

- Base API URL: `http://localhost:8080/task/{TASKID}`
- Task State Endpoint: `http://localhost:8080/task/{TASKID}/taskState`

### Key Files

- `index.js`: Main application entrypoint
- `NamespaceWrappers.js`: API interfaces for task-node interactions
- `coreLogic.js`: Core task logic and functionality implementation

### Deployment Tips

- Obtain a Web3.Storage API key before deployment
- Prepare a K2 wallet for gas fees and bounty funding
- Use the task CLI for publishing to the K2 network