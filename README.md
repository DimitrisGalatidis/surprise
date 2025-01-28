# Multi-Container Docker Setup

This project contains a multi-container setup with a **custom frontend browser container** and a **pre-built backend container (httpbin)** that serves a mock API response. 

The browser container sends an HTTP POST request to httpbin's /anything endpoint with a JSON payload. The httpbin backend:

- Accepts the incoming request.
- Echoes back the JSON payload sent by the browser container.
- The browser container extracts the message field from the echoed response and displays it on the frontend.

## Cloning the Repository

To get started, clone this repository from GitHub:

```bash

git clone https://github.com/DimitrisGalatidis/surprise.git
cd surprise

```

---

## Pulling and Running the Containers

The containers are available on DockerHub. Follow these steps to pull and run them.

### Step 1: Pull the Docker Images

Run the following commands to pull the images from DockerHub:

```bash

docker pull grindev1996/browser-container:latest
docker pull kennethreitz/httpbin

```

### Step 2: Run the Containers

Use the following `docker run` commands to start the containers:

#### Start the Backend Container:

```bash

docker run -d -p 5000:80 --name backend kennethreitz/httpbin

```

#### Start the Browser Container:

```bash

docker run -d -p 8000:8000 --link backend:backend grindev1996/browser-container:latest

```

- **Backend** will run on: `http://localhost:5000`
- **Frontend** will run on: `http://localhost:8000`

### Step 3: Run the App

1. Open a web browser and navigate to `http://localhost:8000`.
2. Now what!?

---

## Using Docker Compose

For convenience, this repository includes a `docker-compose.yml` file. Follow these steps to use it:

### Step 1: Run Docker Compose

Run the following command to start all containers:

```bash

docker-compose up

```
This will:

- Pull the kennethreitz/httpbin backend image from DockerHub.
- Pull and run the custom frontend browser container from DockerHub.

### Step 2: Access the App

1. Open a web browser and navigate to `http://localhost:8000`.
2. The backend API will be available at `http://localhost:5000`.

---

## Important Notes

- Ensure that Docker is installed and running on your machine.
- The backend is powered by the pre-built httpbin image, which echoes back responses sent by the browser container.
- The frontend container depends on the backend container, so ensure both are running simultaneously.




