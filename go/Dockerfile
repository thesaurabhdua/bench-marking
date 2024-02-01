# Use an official Go runtime as a parent image
FROM --platform=linux/amd64  golang:1.20

# Create a directory for the application
RUN mkdir /app

# Set the working directory to your app directory
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . /app

# Expose port 8080 to the outside world
EXPOSE 8080

# Command to run the Go application
CMD ["go", "run", "."]
