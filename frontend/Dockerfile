# Use an official Node.js runtime as a parent image
FROM node:21 AS builder

# Set the working directory inside the container
WORKDIR /app

# Copy only package files first for better caching of npm install
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the app's source code
COPY . .

#Stage 2
FROM node:21-slim

WORKDIR /app

COPY --from=builder /app .

# Expose port if needed (optional)
EXPOSE 5173 

# Start the application
CMD ["npm", "run", "dev", "--", "--host"]

