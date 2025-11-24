# Use a stable Python base image with distutils available
FROM python:3.10-bullseye

# Set working directory inside container
WORKDIR /app

# Install system dependencies (distutils for Django 3.2)
RUN apt-get update && apt-get install -y python3-distutils \
    && rm -rf /var/lib/apt/lists/*

# Install Django directly (no requirements.txt needed)
RUN pip install --no-cache-dir django==3.2

# Copy project files
COPY . /app/

# Expose application port
EXPOSE 8000

# Run migrations and start server at container startup
CMD ["sh", "-c", "python manage.py migrate && python manage.py runserver 0.0.0.0:8000"]
