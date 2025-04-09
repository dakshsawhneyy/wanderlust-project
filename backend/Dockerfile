# Use an official Node.js runtime as a parent image
FROM node:21 AS builder

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .    

# Stage 2
FROM node:21-slim

WORKDIR /app

COPY --from=builder /app .

EXPOSE 5000

CMD ["npm", "start"]

