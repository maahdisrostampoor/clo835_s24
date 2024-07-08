# Use the official Python image from the Docker Hub
FROM python:3.9-slim

# Set the working directory in the container
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . /app

# Install the necessary dependencies
RUN pip install --no-cache-dir tzdata

# Expose the port that the application will run on
EXPOSE 3030

# Define the command to run the application
CMD ["python", "app.py"]

