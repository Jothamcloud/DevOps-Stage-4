FROM python:3.9
WORKDIR /app

# Copy application source
COPY . .

# Install dependencies
RUN pip install -r requirements.txt

# Set environment variables
ARG REDIS_HOST
ARG REDIS_PORT
ARG REDIS_CHANNEL
ENV REDIS_HOST=redis-queue
ENV REDIS_PORT=6379
ENV REDIS_CHANNEL=log_channel

CMD ["python", "processor.py"]