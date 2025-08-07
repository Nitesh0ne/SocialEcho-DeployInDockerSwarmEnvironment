# Stage 1: Build the React app
FROM node:18-alpine AS build

# Set working directory
WORKDIR /app

# Copy source files
COPY package.json package-lock.json ./
RUN npm install --save-dev @babel/plugin-proposal-private-property-in-object

RUN npm install

COPY . .

# Build the React app
RUN npm run build

# Stage 2: Serve with nginx
FROM nginx:alpine

# Remove default nginx static assets
RUN rm -rf /usr/share/nginx/html/*

# Add your custom config
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Copy React build output to nginx's public directory
COPY --from=build /app/build /usr/share/nginx/html

# Copy custom nginx config (optional)
# COPY nginx.conf /etc/nginx/conf.d/default.conf

# Expose port
EXPOSE 80

# Start nginx
CMD ["nginx", "-g", "daemon off;"]
