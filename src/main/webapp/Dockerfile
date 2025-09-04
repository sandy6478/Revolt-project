# Use Python slim base
FROM python:3.11-slim

# Set environment variables (same as x-common-env)
ENV PYTHONUNBUFFERED=1 \
    LANG=C.UTF-8 \
    LC_ALL=C.UTF-8 \
    TZ=UTC

# Set working directory inside the container
WORKDIR /var

# Install system dependencies (if needed later)
RUN apt-get update && apt-get install -y --no-install-recommends \
    gcc \
    curl \
    && rm -rf /var/lib/apt/lists/*

# Copy your app code into container
# (assuming your Python app is in ./app)
COPY ./app /var/app

# Install Python dependencies (if requirements.txt exists)
COPY requirements.txt /var/app/requirements.txt
RUN pip install --no-cache-dir -r /var/app/requirements.txt

# Default command (can be overridden by docker-compose)
CMD ["python", "--version"]
