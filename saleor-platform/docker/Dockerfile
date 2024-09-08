FROM python:3.9-slim

# Install system dependencies
RUN apt-get update && \
    apt-get install -y \
    build-essential \
    libffi-dev \
    libpq-dev \
    gcc \
    g++ \
    pkg-config \
    libcairo2-dev \
    && rm -rf /var/lib/apt/lists/* \
    && pip install --upgrade pip setuptools wheel

# Set the working directory
WORKDIR /app

# Copy requirements.txt
COPY requirements.txt .

# Install Python dependencies with detailed error logs
RUN pip install --no-cache-dir -r requirements.txt 
  
  
# Copy the rest of the application code
COPY . .

# Set the entrypoint
CMD ["python", "app.py"]
