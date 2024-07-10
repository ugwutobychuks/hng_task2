# Use an official Node.js runtime as a parent image
FROM node:14-alpine

# Define environment variable for the API URL
ARG VITE_API_URL
ENV VITE_API_URL=${VITE_API_URL}

# Set the working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Set npm registry to use the official npm registry and install dependencies with retries
RUN npm i --lockfile-version 3 --package-lock-only && \
    npm install --retry 5

# Copy the rest of the application code
COPY . .

# Build the application
RUN npm run build

# Expose the port the app runs on
EXPOSE 3000

# Run the app
CMD ["npm", "run", "preview"]
