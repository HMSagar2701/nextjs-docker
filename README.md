# DockerNextJS App

This is a [Next.js](https://nextjs.org) project bootstrapped with [`create-next-app`](https://nextjs.org/docs/app/api-reference/cli/create-next-app), set up to run inside a Docker container for easy development and deployment.

## Getting Started

### Running the Development Server with Docker

Build the Docker image:

```bash
docker build -t dockernextjs-app .
Run the container, exposing port 3000 and mounting your code for live reload:

bash
Copy
Edit
docker run -p 3000:3000 -v ${PWD}:/app -w /app dockernextjs-app npm run dev
Open http://localhost:3000 in your browser to see the running app.

Editing Your Project
Start editing the page by modifying app/page.tsx. The Next.js development server inside the container will automatically reload your changes.

Building for Production
Build the production image:

bash
Copy
Edit
docker build -t dockernextjs-app-prod -f Dockerfile.prod .
Run the production container:

bash
Copy
Edit
docker run -p 3000:3000 dockernextjs-app-prod
Learn More
To learn more about Next.js, check out:

Next.js Documentation

Learn Next.js

Next.js GitHub repository

Deploy on Vercel
You can also deploy your app on Vercel, the platform made by the creators of Next.js.

See Next.js deployment docs for details.

Sample Dockerfile (Development)
dockerfile
Copy
Edit
# Use official Node.js 18 image
FROM node:18-alpine

# Set working directory
WORKDIR /app

# Install dependencies
COPY package.json yarn.lock* package-lock.json* ./
RUN npm install

# Copy project files
COPY . .

# Expose port 3000
EXPOSE 3000

# Start Next.js development server
CMD ["npm", "run", "dev"]
