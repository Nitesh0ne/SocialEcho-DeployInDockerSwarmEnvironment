FROM node:18-alpine

# Create app directory
WORKDIR /app

# Install app dependencies
COPY package.json package-lock.json ./
RUN npm ci --only=production

# Copy app source code
COPY . .

# Use non-root user for security
RUN addgroup app && adduser -S -G app app
USER app

# Expose app port
EXPOSE 4000

# Start the app
CMD ["npm", "start"]
