Here’s the `README.md` file in a copy-paste-friendly format for the CLI:


# SonarQube Setup with Docker Compose

This repository provides a setup for running a SonarQube server using Docker Compose, along with the SonarQube scanner to analyze your project's code.

## Table of Contents
- Overview
- Requirements
- Setup
- Running SonarQube Server
- Running SonarQube Scanner
- References

## Overview
SonarQube is an open-source platform for continuous inspection of code quality, offering metrics like bugs, vulnerabilities, and code smells.

## Requirements
- Docker and Docker Compose installed.
- SonarQube authentication token.

## Setup

Clone the repository:


git clone https://github.com/<your-username>/sonarqube-project.git
cd sonarqube-project


## Running SonarQube Server

Start the SonarQube server with PostgreSQL:


docker-compose up -d


Access SonarQube dashboard:


http://localhost:9000


Login (default credentials):


Username: admin
Password: admin


Create a new project and generate an authentication token.

## Running SonarQube Scanner

Run the SonarQube scanner against your project:


docker run --rm \
  --network=docker-sonarqube-and-sonarqube-scanner_sonarqube-network \
  -v $(pwd):/usr/src \
  sonarsource/sonar-scanner-cli:latest \
  -Dsonar.projectKey=<name_from_sonarqube:9000> \
  -Dsonar.sources=. \
  -Dsonar.host.url=http://sonarqube:9000 \
  -Dsonar.login=<add_token_from_sonarqube:9000>


Replace `<name_from_sonarqube:9000>` with your project key and `<add_token_from_sonarqube:9000>` with your authentication token.

## References
- SonarQube Documentation: https://docs.sonarqube.org/
- Docker Compose Documentation: https://docs.docker.com/compose/


This format should work well for copying and pasting directly into the CLI or a text editor.
