# Use Node.js image to build the React app
FROM node:20 AS build
WORKDIR /app

# Copy package files and install dependencies
COPY package*.json ./
RUN npm install

# Copy the source code and build the app
COPY . ./
RUN npm run build

# Use NGINX to serve the static files
FROM nginx:stable-alpine
COPY --from=build /app/build /usr/share/nginx/html

# Expose port 80
EXPOSE 80

# NGINX runs by default
