# docker-sample-app
This is the assignment to Deploy a Sample Web Application Using Docker Containers

Step 1: Create a Simple Application

I have created a sample Node.js application. Create a directory for my project and navigate to it in my terminal.
mkdir docker-sample-app
cd docker-sample-app

Inside my project directory, create a simple app.js file with the following content:

const http = require('http');

const server = http.createServer((req, res) => {
  res.writeHead(200, { 'Content-Type': 'text/plain' });
  res.end('Hello, Docker World!\n');
});

const port = process.env.PORT || 3000;
server.listen(port, () => {
  console.log(`Server running on http://localhost:${port}`);
});

This basic Node.js application sets up a web server that responds with “Hello, Docker World!” when accessed.

Step 2: Create a Dockerfile

A Dockerfile is a script that defines the instructions to build a Docker image. Create a file named Dockerfile in my project directory and add the following content:

FROM node:14

WORKDIR /usr/src/app

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 3000

CMD ["node", "app.js"]

This Dockerfile sets up a Node.js environment in a container, copies the application code and dependencies, and specifies how to run the application.

Step 3: Build the Docker Image

With Dockerfile in place, we can build a Docker image for the application. In my project directory, run the following command:

docker build -t docker-sample-app .

Step 4: Run the Docker Container

Now to built the Docker image, we can run a Docker container from it. Use the following command.

docker run -p 3000:3000 docker-sample-app

This command maps port 3000 in the container to port 3000 on the host machine, allowing us to access the application in a web browser.

Step 5: Access the Dockerized Application

Open the web browser and navigate to http://localhost:3000. We should see "Hello, Docker World!" displayed, indicating that Dockerized application is running successfully.





