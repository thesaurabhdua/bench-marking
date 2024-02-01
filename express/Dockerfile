# Use an official Node.js runtime as a base image

FROM --platform=linux/amd64 node:lts-alpine

# Create a directory for the application
RUN mkdir /app

# Set the working directory inside the container
WORKDIR /app

# Copy the rest of your application code to the working directory
COPY . /app

# Install app dependencies
RUN npm install

# Expose the port your app will run on
EXPOSE 4001

# Define the command to run your application
CMD ["npm", "start"]
