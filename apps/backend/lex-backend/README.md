# NestJS with Prisma Setup

This repository provides a NestJS backend with Prisma ORM connected to a Dockerized database. Follow the steps below to get the development environment running from scratch, including installing dependencies, setting up Docker, and configuring Prisma.

## Prerequisites

Before you begin, ensure you have the following installed:

- [Docker](https://www.docker.com/get-started) (for running the database container)
- [Node.js](https://nodejs.org/) (with npm or yarn)
- [NestJS CLI](https://docs.nestjs.com/): Install it globally using npm:
  ```bash
  npm install -g @nestjs/cli
  ```

## Steps to Run the Development Environment

1. Clone the Repository

   Clone the repo to your local machine

   ```bash
   gh repo clone StephanVanHemelrijck/FinalWork.Lexora
   ```

2. Navigate to the backend folder

   ```bash
   cd apps/backend/lex-backend
   ```

3. Install Dependencies

   Install the necessary Node.js dependencies:

   ```bash
   npm install
   ```

   This will install all required packages listed in `package.json`

4. Set up Docker Database

   You need to have Docker running to create a container for your database.

   4.1 Build the docker container

   Since this repository has a docker-compose.yml file, you can build the database container by running:

   ```bash
   docker-compose up -d
   ```

   This will start the container in detached mode. The docker-compose.yml file should define the database service and expose the necessary ports for the NestJS app to connect to.

   4.2 Database configuration in .env

   Ensure that your database connection is configured correctly. Open the `.env` file and set the database connection URL to match your Docker container settings that you can find in the `docker-compose.yml` file under `postgres`. For example:

   ```bash
   DATABASE_URL="postgresql://devuser:devpass@localhost:5432/devdb"
   ```

5. Set up Prisma

   5.1 Generate Prisma Client

   Prisma uses a generated client to interact with the database. To generate this client, run:

   ```bash
   npx prisma generate
   ```

   5.2 Run migrations

   ```bash
   npx prisma db push
   ```
