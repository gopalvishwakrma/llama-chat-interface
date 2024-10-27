# Llama Chat Interface

A full-stack chat interface application using a custom Llama-based backend for language generation and a React-based front end for an interactive chat experience. The backend is containerized using Docker and managed by Docker Compose, making it easy to set up and deploy. The backend runs on an Almalinux-based environment, and the frontend is built with Node.js and React.

## Table of Contents
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Configuration](#configuration)
- [Screenshots](#screenshots)
- [Troubleshooting](#troubleshooting)

## Features
- **Backend with Llama**: Uses Llama-based backend to handle language generation tasks.
- **Frontend UI with React**: A clean and simple chat interface using React and Tailwind CSS.
- **Environment Configuration**: Configure server URLs and other parameters easily with `.env` files.
- **Resource Management**: Specify CPU and memory limits to manage resources for each container.
  
## Prerequisites
Ensure you have the following installed on your machine:
- [Docker](https://www.docker.com)
- [Docker Compose](https://docs.docker.com/compose/)
- Access to a server or local machine with Almalinux 9

## Installation

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yourusername/llama-project.git
   cd llama-project
   ```

2. **Place the Model File**:
   Ensure the model file `llama-3.2-1b-instruct-q8_0.gguf` is in the `models` directory. This file is required for the backend to function.

3. **Build and Start the Containers**:
   Use Docker Compose to build and start the containers.
   ```bash
   docker compose build --no-cache
   docker compose up -d
   ```

   **Note**: The `--no-cache` option ensures that the images are built without using cache.

## Usage
Once the containers are running:
1. **Access the Llama Chat Interface** by navigating to [http://your_ip_address:3000](http://your_ip_address:3000) in a web browser.
2. **Interact with the Chat**: Type your queries in the chat interface, and the backend will generate responses.

## Project Structure
```plaintext
├── docker-compose.yml           # Docker Compose file for managing services
├── Dockerfile.llama              # Dockerfile for the Llama backend
├── Dockerfile.ui                 # Dockerfile for the React-based frontend
├── models/
│   └── llama-3.2-1b-instruct-q8_0.gguf  # Model file required for Llama
└── ui/
    ├── package.json              # Package configuration for the UI
    ├── public/
    │   └── index.html            # HTML entry point for the React app
    ├── src/
    │   ├── App.js                # Main React component
    │   ├── components/
    │   │   └── ChatInterface.jsx # Chat interface component
    │   └── index.js              # Main entry point for React
    └── tailwind.config.js        # Tailwind CSS configuration
```

## Configuration
### Environment Variables
Configuration variables are managed through the `.env` file located in the `ui` directory. Below are the available options:

```plaintext
REACT_APP_API_URL=http://your_ip_address:8080
REACT_APP_TITLE=Llama Chat Interface
REACT_APP_MAX_TOKENS=400
```

Ensure that the `REACT_APP_API_URL` points to the backend service.

## Screenshots
Here’s how the application looks at various stages.

### Chat Interface
![Chat Interface](assets/Interface-screenshot.png)

### Backend Log Example
![Backend Logs](assets/Backend-screenshot.png)

## Troubleshooting

- **Error: Model file not found**:
  - Ensure the model file `llama-3.2-1b-instruct-q8_0.gguf` is located in the `models` directory.

- **Backend Not Responding**:
  - Verify that the backend container is running and accessible on port 8080.

- **Network Issues Between Containers**:
  - Confirm that the containers are on the same Docker network (`llama-network`).

