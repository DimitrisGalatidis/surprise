# Multi-Container Docker Setup: Star Wars-Themed App

This project contains a multi-container setup with a **frontend browser container** and a **backend API container**. The browser container displays a message, while the backend container serves the message to the frontend.

## Cloning the Repository

To get started, clone this repository from GitHub:

```bash

git clone https://github.com/DimitrisGalatidis/surprise.git
cd surprise

```

---

## Pulling and Running the Containers

Follow these steps to pull and run the images from DockerHub.

### Step 1: Pull the Docker Images

Run the following commands to pull the images from DockerHub:

```bash

docker pull grindev1996/browser-container:latest
docker pull grindev1996/custom-backend:latest

```

### Step 2: Run the Containers

Use the following `docker run` commands to start the containers:

#### Start the Backend Container:

```bash

docker run -d -p 5000:5000 grindev1996/custom-backend:latest

```

#### Start the Browser Container:

```bash

docker run -d -p 8000:8000 --link backend:backend grindev1996/browser-container:latest

```

- **Backend** will run on: `http://localhost:5000/api`
- **Browser container** will run on: `http://localhost:8000`

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

### Step 2: Access the App

1. Open a web browser and navigate to `http://localhost:8000`.
2. The backend API will be available at `http://localhost:5000/api`.

---

## Important Notes

- Ensure that Docker is installed and running on your machine.
- The frontend container depends on the backend container, so ensure both are running simultaneously.


