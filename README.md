# 🐳 Dockerized Next.js App

This is a [Next.js](https://nextjs.org) project bootstrapped with [`create-next-app`](https://nextjs.org/docs/app/api-reference/cli/create-next-app), containerized using Docker for smooth development and production workflows.

---

## 🚀 Getting Started (Development)

### 1️⃣ Build the Docker image:

```bash
docker build -t dockernextjs-app .

docker run -p 3000:3000 -v ${PWD}:/app -w /app dockernextjs-app npm run dev
🧠 This command:

Maps port 3000 from the container to your machine

Mounts your current directory (${PWD}) into the container for live development

Runs npm run dev inside /app

🔗 Open http://localhost:3000 to see your app running.

🛠️ Editing Your Project
You can modify the app by editing app/page.tsx (or any other page/component). Changes will automatically reflect in the browser thanks to Next.js hot reloading.

docker run -p 3000:3000 dockernextjs-app-prod
📦 Sample Dockerfile (Development)

# Use official Node.js 18 image
FROM node:18-alpine

# Set working directory
WORKDIR /app

# Install dependencies
COPY package.json yarn.lock* package-lock.json* ./
RUN npm install

# Copy project files
COPY . .

# Expose port
EXPOSE 3000

# Start development server
CMD ["npm", "run", "dev"]