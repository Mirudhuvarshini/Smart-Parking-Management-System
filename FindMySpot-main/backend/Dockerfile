FROM python:3.10-slim

WORKDIR /app

# Install system dependencies
RUN apt-get update && apt-get install -y libgl1 libglib2.0-0 && rm -rf /var/lib/apt/lists/*

# Install python dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy complete application
COPY . .

# Expose port
ENV PORT 5000
EXPOSE ${PORT}

# Run with Gunicorn
CMD gunicorn --bind 0.0.0.0:$PORT --workers 1 --timeout 300 app:app
