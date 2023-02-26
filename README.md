# NodeJs-Simple-App

A simple Node.js application using MongoDB and Docker that takes user inputs such as Name, Email, and favorite football team, and saves it to a MongoDB database.

## Project Structure

```
NodeJs-Simple-App/
├── Dockerfile
├── docker-compose.yml
├── app/
│   └── index.js
├── node_modules/
├── package.json
└── package-lock.json
```

## Prerequisites

Make sure you have the following installed:
- Node.js
- npm (Node Package Manager)
- Docker
- Docker Compose

## Setup Instructions

1. **Clone the repository**

    ```bash
    git clone https://github.com/akintunero/NodeJs-Simple-App.git
    cd NodeJs-Simple-App
    ```

2. **Initialize the project and install dependencies**

    ```bash
    npm init -y
    npm install express mongoose
    ```

3. **Create a Docker network**

    ```bash
    docker network create myapp-network
    ```

4. **Run MongoDB container**

    ```bash
    docker run -d --name mongo --network myapp-network mongo
    ```

5. **Build the Docker image for the Node.js app**

    ```bash
    docker build -t nodejs-simple-app .
    ```

6. **Run the Node.js application container**

    ```bash
    docker run -d --name nodejs-simple-app --network myapp-network -p 3000:3000 nodejs-simple-app
    ```

7. **Verify that the containers are running**

    ```bash
    docker ps
    ```

8. **Access the application**

   Open your browser and navigate to [http://localhost:3000](http://localhost:3000).

## Application Endpoints

- `GET /` - Returns "Hello World!".
- `POST /users` - Adds a new user to the database. Expects a JSON body with `name`, `email`, and `favoriteTeam`.
- `GET /users` - Retrieves all users from the database.

## Example cURL Commands

- **Test the root endpoint**

    ```bash
    curl http://localhost:3000
    ```

- **Add a new user**

    ```bash
    curl -X POST http://localhost:3000/users -H "Content-Type: application/json" -d '{"name":"John Doe","email":"john.doe@example.com","favoriteTeam":"Manchester United"}'
    ```

- **Get all users**

    ```bash
    curl http://localhost:3000/users
    ```

#