# System Description
This application was developed during the [Santander Dev Week 2024](https://github.com/digitalinnovationone/santander-dev-week-2024) by the DIO platform.

The application allows users to select a champion from League of Legends, ask a question, and receive a response from a Chat Completion model that impersonates the selected champion.

# Front-end

![HTML5](https://img.shields.io/badge/html5-%23E34F26.svg?style=for-the-badge&logo=html5&logoColor=white) ![CSS3](https://img.shields.io/badge/css3-%231572B6.svg?style=for-the-badge&logo=css3&logoColor=white) ![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E)

This front-end application was developed using the [Horizontal Timeline](https://github.com/digitalinnovationone/santander-dev-week-2024) theme to display League of Legends champions in a carousel format.

![Screenshot 01 of the Home page](https://raw.githubusercontent.com/Joao-Lucas-de-Oliveira-Lima/lol-chat-frontend/refs/heads/main/images/screenshot_01.png)
![Screenshot 02 of the Home page](https://raw.githubusercontent.com/Joao-Lucas-de-Oliveira-Lima/lol-chat-frontend/refs/heads/main/images/screenshot_02.png)

# Running the Application
To run the application, simply open the `index.html` file located in the project's root directory in a web browser.

If you are running a local environment, update the API endpoint in `src/scripts/api.js` by modifying the route attributes to match your local server URL. By default, the endpoint is set to:

```
http://localhost:8080/champions
```
# Back-end
![Java](https://img.shields.io/badge/Java-%23F89820.svg?style=for-the-badge&logo=openjdk&logoColor=white) ![Spring](https://img.shields.io/badge/Spring-%238BC34A.svg?style=for-the-badge&logo=spring&logoColor=white) ![Swagger](https://img.shields.io/badge/Swagger-%238D6E63.svg?style=for-the-badge&logo=swagger&logoColor=white) ![Docker](https://img.shields.io/badge/Docker-%232496ED.svg?style=for-the-badge&logo=docker&logoColor=white)
## About the API

A REST API developed using Java Spring that enables users to interact with League of Legends (LoL) champions through a chat completion service.

# Installation Guide

## 1. Running the Application with Docker Compose

### Prerequisites
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)

### Steps

#### 1. Obtain an API Key for the Chat Completion Service

This API connects to the Llama3-8b-8192 model provided by Groq Cloud. To acquire an API key, follow [these instructions](https://console.groq.com/keys) and add the key to the `CHAT_SERVICE_KEY` environment variable in the `docker-compose.yaml` file. Also, set the `CHAT_SERVICE_URL` accordingly.

#### 2. Starting the Application
Run the following command to start the containers:

```bash
docker-compose up -d
```

By default, the application will be available at `http://localhost:8080`.

### Clean Architecture
![REST API Architectural Diagram](https://raw.githubusercontent.com/Joao-Lucas-de-Oliveira-Lima/lol-chat-backend-spring/017d53a728cb53e8fd6565276ee8d4bd80856072/docs/images/architectural-diagram.png)

The project structure includes five main directories:
- `application`: Contains use cases and interfaces for accessing resources such as databases and HTTP clients.
- `domain`: Defines system entities and business-rule exceptions.
- `infrastructure`: Implements the application layer's gateways, providing access to databases, repositories, HTTP client interfaces, controllers, DTOs, framework-specific exceptions, and other Spring resources.
- `configuration`: Holds configuration files with dependency injection beans.
- `shared`: Contains utility classes accessible across multiple layers.

# Tests

## Running Tests
### Prerequisites

- [Java 21](https://www.oracle.com/br/java/technologies/downloads/#java21)
- [Docker Desktop](https://www.docker.com/products/docker-desktop/) (required for integration tests)

Run the following commands in the terminal from the application's root directory:

- **Only unit tests:**

```bash
./mvnw test
```

- **For integration and unit tests:**
```bash
./mvnw verify
```

> **Note:** Ensure Docker is running, as the application uses TestContainers to create a PostgreSQL database in Docker for each integration test class.

# Documentation

## API Endpoints Preview
```text
GET /champions - Retrieve a list of champions.

POST /champions/ask/{id} - Ask a question to a specific champion by ID and retrieve the champion's response.
```

## OpenAPI Documentation
- To view the full API documentation, including endpoints and data schemas, open the Swagger UI at:
  `/swagger-ui/index.html`

- For API documentation in JSON format suitable for tools like Postman, Insomnia, and other API clients, visit: `/v3/api-docs`.

---
