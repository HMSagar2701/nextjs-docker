# 🐳 Dockerized Next.js App

This is a [Next.js](https://nextjs.org) project bootstrapped with [`create-next-app`](https://nextjs.org/docs/app/api-reference/cli/create-next-app), containerized using Docker for smooth development and production workflows.

---

## 🚀 Getting Started (Development)

### 1️⃣ Build the Docker image:

```bash
docker build -t dockernextjs-app .
2️⃣ Run the container with live reload:
bash
Copy
Edit
docker run -p 3000:3000 -v ${PWD}:/app -w /app dockernextjs-app npm run dev
🧠 This command:

Maps port 3000 from the container to your machine

Mounts your current directory (${PWD}) into the container for live development

Runs npm run dev inside /app

🔗 Open http://localhost:3000 to see your app running.

🛠️ Editing Your Project
You can modify the app by editing app/page.tsx (or any other page/component). Changes will automatically reflect in the browser thanks to Next.js hot reloading.

🏗️ Building for Production
1️⃣ Build a production-ready Docker image:
bash
Copy
Edit
docker build -t dockernextjs-app-prod -f Dockerfile.prod .
2️⃣ Run the production container:
bash
Copy
Edit
docker run -p 3000:3000 dockernextjs-app-prod
📦 Sample Dockerfile (Development)
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

# Expose port
EXPOSE 3000

# Start development server
CMD ["npm", "run", "dev"]
📚 Learn More
📘 Next.js Documentation

📙 Learn Next.js (Interactive)

🐙 Next.js GitHub Repository

☁️ Deploy on Vercel
You can deploy this app effortlessly on Vercel, the platform by the creators of Next.js.

📄 Read the Next.js deployment docs for more details.

🗂 Recommended .dockerignore
dockerignore
Copy
Edit
node_modules
.next
.git
Dockerfile
.dockerignore
*.log
.env
