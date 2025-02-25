# Build Stage
FROM node:14-alpine AS build-stage

# Set working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application
COPY . .

# Build the Vue.js application
RUN npm run build

# Production Stage: Serve using Nginx
FROM nginx:alpine AS production-stage

# Set working directory
WORKDIR /usr/share/nginx/html

# Remove default Nginx static files
RUN rm -rf ./*

# Copy the built frontend from the build stage
COPY --from=build-stage /app/dist ./

# Expose the port Vue.js runs on
EXPOSE 80

# Set default environment variables (can be overridden at runtime)
ENV PORT=80 \
    AUTH_API_ADDRESS=http://auth-api:8081 \
    TODOS_API_ADDRESS=http://todos-api:8082

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]
