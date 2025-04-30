# Prometheus: Add README for task-template

## Project Overview

This project is a template for creating decentralized tasks on the Koii Network, providing a standardized framework for developing and deploying distributed computational tasks with gradual consensus.

### Purpose
The K2-Task-Template enables developers to create blockchain-based tasks that run on a distributed network of nodes, following a structured, periodic round-based execution model. It provides a comprehensive toolkit for building decentralized applications that can perform computational work, submit results, and manage rewards across a network of participants.

### Key Features
- **Periodic Task Execution**: Tasks run in predefined time-based rounds, ensuring synchronized network participation
- **Flexible Core Logic**: Customizable task, submission, validation, and distribution mechanisms
- **Decentralized Consensus**: Built-in support for task validation and auditing
- **Multi-Stage Task Management**: Supports complex workflows including task execution, submission, distribution, and auditing
- **Easy Deployment**: Simplified deployment to the K2 Settlement Layer with integrated CLI tools
- **Local Development Support**: Docker-based local testing environment
- **WebSocket and REST API Integration**: Enables communication across different network components

### Benefits
- Reduced centralization risk through distributed task processing
- Transparent and verifiable task execution
- Flexible reward distribution mechanisms
- Standardized framework for building decentralized applications
- Simplified development of blockchain-based computational tasks

## Getting Started, Installation, and Setup

### Prerequisites

Before getting started, ensure you have the following requirements:
- Node.js (version 16.0.0 or higher)
- Docker Compose
- A web3.storage account (optional, for IPFS storage)

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

#### Running the Application

You have two runtime options:

1. Global Timers Mode (Default):
   ```bash
   # Set GLOBAL_TIMERS="true" in .env-local
   docker-compose up
   ```

2. Manual Call Mode:
   ```bash
   # Set GLOBAL_TIMERS="false" in .env-local
   docker-compose up
   ```

#### Building the Project

To create a bundled executable for deployment:
```bash
yarn webpack
```

### Deployment Preparation

1. Prepare your Koii wallet
   - Generate a wallet using Koii CLI or use an existing one
   - Locate your wallet's keypair path

2. Obtain Web3.Storage API Key (optional)
   - Create an account at web3.storage
   - Generate an API key

3. Deploy to K2 Testnet:
   ```bash
   npx @_koii/create-task-cli
   ```

### Local Node Testing

1. Copy your wallet to the `config` folder as `id.json`
2. Update `.env-local` with your Task ID
3. Start the local node:
   ```bash
   docker-compose up
   ```

### Accessing API Endpoints

- Base URL: `http://localhost:8080/task/{TASKID}`
- Task State: `http://localhost:8080/task/{TASKID}/taskState`

### Important Notes

- Restart the task node after code modifications
- Use `yarn webpack` to bundle latest changes before redeploying

## Task Lifecycle

The task lifecycle in this system follows a structured process involving multiple stages of submission, validation, and distribution. Here's a detailed breakdown:

### Task Submission Stage
- Participants perform a task and generate a submission value
- The `submitTask()` method is used to submit the task
- Submission involves:
  - Generating a submission value (in this example, a random hash)
  - Storing the submission in a local database
  - Checking and updating the round for the submission

### Audit Stage
- After task submission, an audit process is initiated
- The `auditTask()` method manages the node validation process
- Key audit characteristics:
  - Nodes validate submissions from other participants
  - Voting occurs on the validity of submissions
  - A participant cannot vote on their own submission
  - The `validateNode()` method determines submission validity
    - By default, returns `true` (placeholder for custom validation logic)

### Distribution List Generation
- Nodes generate a distribution list based on submission audits
- The `generateDistributionList()` method creates the list with these principles:
  - Considers submissions from the previous round
  - Checks audit triggers for each submission
  - Calculates votes for each submission
  - Generates a distribution list of valid participants

### Distribution List Submission and Audit
- The `submitDistributionList()` method handles distribution list upload
- Nodes can upload and submit their generated distribution list on-chain
- A separate audit process `auditDistribution()` validates the distribution list
  - Compares generated distribution lists
  - Votes on the validity of distribution lists

### Voting and Validation Mechanisms
- Uses a round-based system for tracking submissions and audits
- Supports voting mechanisms for both task submissions and distribution lists
- Implements shallow comparison for distribution list validation

This lifecycle ensures a decentralized, auditable process for task completion and reward distribution.

## Reward System

The reward system in this project is designed to fairly distribute rewards among task participants through a multi-step validation and distribution process.

### Reward Distribution Mechanism

Rewards are distributed through a structured workflow that involves several key stages:

1. **Submission Validation**
   - Participants submit their work for a specific round
   - Other nodes audit and vote on the validity of submissions
   - Submissions with positive votes are considered for rewards

2. **Distribution List Generation**
   - A selected node generates a distribution list based on validated submissions
   - The distribution list maps participant public keys to reward allocations
   - By default, validated submissions receive an equal reward (1 unit)

3. **Distribution List Validation**
   - Other nodes independently validate the generated distribution list
   - The list is cross-checked against the node's own generation logic
   - This ensures fairness and prevents manipulation of reward allocation

4. **On-Chain Submission**
   - The validated distribution list is submitted to the blockchain
   - This creates a transparent and immutable record of reward distribution

### Key Validation Criteria

- Participants cannot vote on their own submissions
- Submissions undergo a voting mechanism where valid votes determine eligibility
- Nodes can raise audit triggers for suspicious submissions
- The distribution list generation considers audit vote counts

### Reward Allocation Rules

- Equal reward allocation for valid submissions
- Submissions with negative audit votes are excluded from rewards
- The system is designed to be flexible and can be customized based on specific task requirements

*Note: The actual reward amount and specific validation rules can be modified in the `coreLogic.js` file.*

## Task Variables

The task requires the following environment and system variables:

### Global Variables
- `WEB3.STORAGE SECRET KEY`: Used to connect to web3.storage

### Task Variables
- `SCAPING URL`: URL from which data will be scraped

### System Requirements
#### Hardware
- **CPU**: 4-core processor
- **RAM**: 5 GB
- **Storage**: Unspecified test configuration

#### System Specifications
- **Network**: Test configuration
- **Architecture**: AMD
- **Operating System**: OSX

### Task Configuration
- **Task Name**: Your-task-name
- **Task Description**: This task is to test out the namespace function
- **Executable Network**: DEVELOPMENT
- **Round Time**: 600 slots (approximately 2.4 seconds per slot)
- **Audit Window**: 200 slots
- **Submission Window**: 200 slots

### Stake and Bounty Parameters
- **Minimum Stake Amount**: 5 KOII
- **Total Bounty Amount**: 10 KOII
- **Bounty per Round**: 1 KOII
- **Allowed Failed Distributions**: 4

### Additional Configuration
- **Web3.Storage Key**: Must be provided
- **Audit Program ID**: 'main'
- **Space Allocation**: 10 MB

## Additional Notes

### Task Configuration Considerations

When configuring your task, pay special attention to the following key parameters in the `config-task.yml`:

- **Round Time**: Set to 600 slots (approximately 2.4 seconds per slot), which defines the total duration of each task round.
- **Audit and Submission Windows**: Allocated 200 slots each for auditing and submission processes.
- **Minimum Stake**: 5 KOII tokens required to participate in the task.
- **Bounty Structure**: 
  - Total bounty of 10 KOII
  - 1 KOII distributed per round

### Environment and Deployment Flexibility

The task template supports multiple deployment networks:
- Development mode
- Arweave
- IPFS

Developers can customize the task using:
- Environment variables in `.env-local`
- Configuration parameters in `config-task.yml`

### Performance and Resource Requirements

Recommended system specifications:
- CPU: 4-core processor
- RAM: 5 GB
- Storage: 10 MB available
- Recommended OS: OSX
- Architecture: AMD

### API and Interaction

Default API endpoint structure:
- Base URL: `http://localhost:8080/task/{TASKID}`
- Task State Endpoint: `http://localhost:8080/task/{TASKID}/taskState`

### Security and Secrets Management

The template supports custom secrets management through environment variables, allowing secure handling of sensitive configuration details like API keys.

### Monitoring and Debugging

Key monitoring options:
- Console output during local docker-compose runs
- Task state APIs
- Detailed logging in task execution components

### Compatibility Notes

- Requires Node.js version 16.0.0 or higher
- Docker Compose is necessary for local development and testing

## Contributing

We welcome contributions to this project! Here are some guidelines to help you get started:

### Code Style
- We use Prettier for code formatting. Refer to the `.prettierrc` configuration in the repository.
- Key styling rules include:
  - Use 2 spaces for indentation
  - Use single quotes
  - Semicolons are required
  - Trailing commas are used
  - Arrow function parameters can be omitted when possible

### Development Setup
1. Ensure you have the following prerequisites:
   - Node.js version 16.0.0 or higher
   - Docker Compose

2. Fork the repository and clone your fork
3. Install dependencies using `yarn`

### Testing
- Write unit tests for core logic functions
- Use the `tests/unitTest.js` file for implementing tests
- Run tests before submitting a pull request

### Contribution Process
1. Create a new branch for your feature or bugfix
2. Make your changes
3. Run `yarn webpack` to bundle your changes
4. Ensure all tests pass
5. Submit a pull request with a clear description of your changes

### Code Review Process
- All contributions will be reviewed by the maintainers
- Provide a clear and descriptive explanation of your changes
- Be prepared to make modifications based on feedback

### Reporting Issues
- Use the GitHub Issues section to report bugs or suggest improvements
- Include detailed information about the issue, including steps to reproduce
- Provide relevant error messages or screenshots when applicable

### Important Notes
- Familiarize yourself with the project's core logic in `coreLogic.js`
- Understand the task lifecycle and runtime options before contributing
- Follow the existing code structure and patterns in the project

## License

This project is licensed under the ISC License. 

The ISC License is a permissive free software license published by the Internet Systems Consortium (ISC). It is functionally equivalent to the MIT License and is known for its simplicity.

Key points of the ISC License:
- Allows commercial and non-commercial use
- Permits modification and distribution
- Requires preservation of copyright and license notices
- Provides the software "as is" with no warranties

For the full license text, refer to the standard ISC License terms.