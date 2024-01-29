# Use the official Node.js Alpine image as the base image
FROM node:16-alpine
# Set the working directory inside the container
WORKDIR /app
# Copy the package.json and package-lock.json files to the working directory
COPY ./package.json ./
# Install the dependencies
RUN npm install
# Copy the rest of the application code to the working directory
COPY . .
# Build the React application
RUN npm run build

# Set the base image to nginx
FROM nginx
# Expose the port on which the application will run
EXPOSE 3000
# Copy the nginx configuration file to the container
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
# Copy the build output to the nginx public folder
COPY --from=builder /app/build /usr/share/nginx/html

