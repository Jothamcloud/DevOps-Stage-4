# Use Node.js as the base image
FROM node:14-alpine AS build

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json first (for better caching)
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the entire frontend project into the container
COPY . .

RUN npm run build
# Expose the port your frontend app runs on
EXPOSE 8080

# Run the frontend in development mode to access environment variables
CMD ["npm", "run", "dev"]
