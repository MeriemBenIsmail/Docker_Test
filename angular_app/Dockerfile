# Stage 1: Build the Angular app
FROM node:14.17-alpine AS builder

WORKDIR /app

# Copy package.json and package-lock.json to the container
COPY package.json ./

# Install dependencies
RUN npm install

# Copy the entire project to the container
COPY . .

# Build the Angular app
RUN npm run build --prod

# Stage 2: Serve the built app
FROM node:14.17-alpine

WORKDIR /app

# Install http-server globally
RUN npm install -g http-server

# Copy the built app from the builder stage to the current stage
COPY --from=builder /app/dist/angular_app .

# Expose port 4200 for the Angular app
EXPOSE 4200

# Start the http-server to serve the Angular app
CMD ["http-server", "-p", "4200"]
