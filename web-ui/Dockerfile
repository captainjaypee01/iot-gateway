# Use a Node.js base image
FROM node:18-alpine

# Set the working directory
WORKDIR /app

# Copy the package.json and package-lock.json files
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the React app source code
COPY . .

# Build the React app
RUN npm run build

# Use a lightweight web server to serve the built app
FROM nginx:alpine

# Copy the built static files to the appropriate location within the container
COPY --from=0 /app/build /usr/share/nginx/html

# Expose the port for the web server
EXPOSE 3000

# Start the web server
CMD ["nginx", "-g", "daemon off;"]

# # Specify the command to start the frontend application
# CMD ["npm", "start"]