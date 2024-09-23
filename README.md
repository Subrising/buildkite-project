# Buildkite Pipeline Project

## Overview

This project demonstrates the creation of a Buildkite pipeline for a simple Go application. The pipeline builds the application, allows for user input, runs the program, and generates a report. This README documents the process of creating the pipeline, challenges encountered, and potential future improvements.

## Pipeline Structure

The pipeline consists of the following main steps:

1. Build Go Project
2. Manual Approval
3. User Name Input
4. Run the Program
5. Generate Report

## Development Process

### Initial Setup

1. Created a basic Go application in the `hello` directory.
2. Set up a Buildkite account and connected it to the GitHub repository.

### AWS EC2 Setup

1. Created a EC2 instance with a public IP address.
2. Connected to the instance using SSH and installed the Buildkite Docker agent.

### Pipeline Creation

1. Started with a basic pipeline that built and ran the Go application.
2. Gradually added steps for manual approval, user input, and report generation.

### Challenges and Solutions

#### Docker Integration

- **Challenge**: Ensuring the Go build environment was consistent.
- **Solution**: Utilised Docker to create a consistent build environment.

#### Artifact Handling

- **Challenge**: Correctly uploading and downloading the built executable.
- **Solution**: Used Buildkite's artifact commands to manage file transfers between steps.

#### User Input

- **Challenge**: Incorporating user input into the pipeline.
- **Solution**: Implemented a block step to pause the pipeline and collect user input.

#### Variable Expansion

- **Challenge**: Properly expanding variables in pipeline commands.
- **Solution**: Used heredocs with careful escaping to ensure variables were expanded correctly.

#### Report Generation

- **Challenge**: Creating and uploading a report with dynamic content.
- **Solution**: Developed a bash script within the pipeline to generate, upload, and track the report.

## Key Components

### .buildkite/pipeline.yml

This file defines the entire pipeline structure. Key sections include:

- Docker plugin configuration for the build step
- Block step for manual approval and user input
- Command steps for running the program and generating reports

### Go Application

Located in the `hello` directory, this simple application is the core of what the pipeline builds and runs.

## Lessons Learned

1. The importance of proper variable expansion in Buildkite pipelines.
2. Effective use of Buildkite's artifact and metadata features.
3. Balancing between inline scripts and separate script files for pipeline steps.
4. The value of iterative development and testing when creating pipelines.

## Potential Future Improvements

1. Implement more comprehensive error handling and logging.
2. Add unit tests for the Go application and integrate them into the pipeline.
3. Explore Buildkite's plugin ecosystem for additional functionality.
4. Implement caching mechanisms to speed up the build process.
5. Add more sophisticated reporting, possibly integrating with external tools.
6. Utilise the retry component of Buildkite to ensure that failed steps are retried.
