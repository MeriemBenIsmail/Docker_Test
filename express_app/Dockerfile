# Stage 1: Build the Express app
FROM node:14.17-alpine AS builder

WORKDIR /app

# Copy package.json and package-lock.json to the container
COPY package.json ./

# Install dependencies
RUN npm install

# Copy the entire project to the container
COPY . .

# Stage 2: Run the Express app
FROM node:14.17-alpine

WORKDIR /app

# Copy the built app from the builder stage to the current stage
COPY --from=builder /app .

# Expose port 3000 for the Express app
EXPOSE 3000

# Start the Express app
CMD ["npm", "start"]
