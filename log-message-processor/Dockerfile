FROM python:3.9

# Set the working directory
WORKDIR /app

# Copy the requirements file
COPY requirements.txt .

# Upgrade pip and install dependencies
RUN pip install --upgrade pip && \
    pip install redis>=5.0.0 requests>=2.31.0 thriftpy2>=0.4.16 py_zipkin --upgrade

# Copy the application code
COPY . .

# Run the application
CMD ["python", "main.py"]
