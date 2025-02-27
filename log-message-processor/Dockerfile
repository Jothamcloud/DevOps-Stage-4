FROM python:3.8-slim

# Install necessary development libraries
RUN apt-get update && apt-get install -y build-essential libssl-dev

# Copy and install Python dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of your application code
COPY . .

# Set runtime command
CMD ["python", "main.py"]