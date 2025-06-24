# Overview of Agents in Digital Storefront

This document outlines the LLM-based and autonomous agents used within the Digital Storefront project. It serves as a reference for contributors and AI tooling, detailing the roles, triggers, behaviors, and outputs of each agent. This documentation aids in understanding and reproducing the behavior of these agents.

## Table of Agents

| Name    | Description                                                  | Trigger                       |
|---------|-------------------------------------------------------------|-------------------------------|
| DocWriter | Generates documentation files for the project           | Command to generate docs      |
| ReadmeGenerator | Creates README files based on project structure   | New project creation          |
| TestGenerator | Generates test cases for components and pages       | Pull request for new features |

### DocWriter

**Name**: DocWriter

**Description**: The DocWriter agent automatically generates documentation files based on the existing project structure, ensuring consistency and up-to-date content.

**Trigger**: Activated when a command to generate documentation is issued.

**Inputs and Outputs**:
- **Inputs**: Project structure, existing documentation formats.
- **Outputs**: Generated documentation files (e.g., Markdown files).

**Where the Logic Lives**: `/agents/doc-writer.ts`

**Review or Audit Process**: Generated documents are reviewed by the project maintainers before merging.

### ReadmeGenerator

**Name**: ReadmeGenerator

**Description**: The ReadmeGenerator agent is responsible for creating standardized README files for new repositories based on templates and existing project data.

**Trigger**: Triggered when a new repository is created or when the `generate-readme` command is issued.

**Inputs and Outputs**:
- **Inputs**: Repository metadata (name, description), project features,
- **Outputs**: A generated README.md file.

**Where the Logic Lives**: `/agents/readme-generator.ts`

**Review or Audit Process**: The generated README is reviewed by the project manager before being committed to the repository.

### TestGenerator

**Name**: TestGenerator

**Description**: The TestGenerator agent generates test cases based on existing components and page structures to ensure comprehensive test coverage.

**Trigger**: Triggered on pull requests containing new features or components.

**Inputs and Outputs**:
- **Inputs**: Component structure, required functionalities.
- **Outputs**: Generated test files for unit and integration tests.

**Where the Logic Lives**: `/agents/test-generator.ts`

**Review or Audit Process**: Tests will be reviewed during the code review process and adjusted as needed before merging.

## How to Invoke Agents

### DocWriter
- **CLI**: Use the command `npm run generate-docs` to invoke DocWriter.
- **CI**: Automatically triggered in the CI/CD pipeline when documentation updates are required.
- **Prompts**: Not applicable for this agent.

### ReadmeGenerator
- **CLI**: Use `npm run generate-readme` to invoke ReadmeGenerator.
- **Pull Requests**: Automatically runs on new repository creation.

### TestGenerator
- **CLI**: Use the command `npm run generate-tests` to run the TestGenerator.
- **CI**: Runs as part of the CI process when testing is initiated.

## Future Agent Proposals

### Proposed NotificationAgent
- **Name**: NotificationAgent
- **Description**: This agent will handle notifications for users based on their preferences and system events.
- **Trigger**: To be triggered based on specific events in the application.
- **Inputs and Outputs**: Input will include user preferences and event data; Output will be notification messages sent via email or in-app notifications.

### Contribution Instructions for New Agents

To add a new agent to this documentation, follow these steps:
1. Identify the agent's role, trigger, and behavior.
2. Add the agent to the Table of Agents.
3. Create a detailed section for the agent following the format provided.
4. Update the 'How to Invoke Agents' section if applicable.
5. Submit a pull request with the updated `AGENTS.md` file.
