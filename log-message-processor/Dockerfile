FROM python:3.9-slim

WORKDIR /app

# Copy requirements file and install dependencies
COPY log-message-processor/requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy project files
COPY log-message-processor/ .

CMD ["python", "main.py"]