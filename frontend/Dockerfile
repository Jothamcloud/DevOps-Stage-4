FROM node:12 as build-stage

WORKDIR /app

# Copy package files and install dependencies
COPY frontend/package*.json ./
RUN npm install

# Copy project files and build
COPY frontend/ .
RUN npm run build

# Production stage
FROM nginx:stable-alpine as production-stage
COPY --from=build-stage /app/dist /usr/share/nginx/html

# Copy custom nginx configuration
COPY frontend/nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 8080

# Create a custom entrypoint script to run nginx on the specified port
RUN echo '#!/bin/sh\n\
sed -i "s/listen 80/listen $PORT/g" /etc/nginx/conf.d/default.conf\n\
nginx -g "daemon off;"' > /docker-entrypoint.sh && \
chmod +x /docker-entrypoint.sh

CMD ["/docker-entrypoint.sh"]