# Base image
FROM node:18-alpine

# Set working directory
WORKDIR /app

# Install app dependencies
COPY package.json package-lock.json ./
RUN npm install

# Copy source code
COPY . .

# Expose backend port (adjust if your server uses another)
EXPOSE 4000

# Start the app
CMD ["npm", "Start"]
