FROM python:3.10-bullseye

# Set working directory
WORKDIR /app

# Install distutils (needed for Django 3.2)
RUN apt-get update && apt-get install -y python3-distutils \
    && rm -rf /var/lib/apt/lists/*

# Copy requirements first (if you have one)
COPY requirements.txt .

# Install Python dependencies
RUN pip install --no-cache-dir -r requirements.txt || pip install django==3.2

# Copy project files
COPY . .

# Expose application port
EXPOSE 8000

# Run migrations and start server at container startup
CMD ["sh", "-c", "python manage.py migrate && python manage.py runserver 0.0.0.0:8000"]
