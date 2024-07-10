# Use the official Node.js 16 image
FROM node:16

# Set the working directory in the container
WORKDIR /app

# Copy the package.json and package-lock.json files
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the application
RUN npm run build

# Expose the port the app runs on
EXPOSE 3000

# Set the environment variable for Vite API URL
ARG VITE_API_URL
ENV VITE_API_URL=$VITE_API_URL

# Command to run the application
CMD ["npm", "run", "preview"]
