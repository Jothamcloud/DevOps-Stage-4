FROM node:12

WORKDIR /app

# Copy package files and install dependencies
COPY package*.json ./
RUN npm install

# Copy project files
COPY todos-api/ .

EXPOSE 8082

CMD ["npm", "server.js"]