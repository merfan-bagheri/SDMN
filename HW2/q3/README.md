# Get the current status
curl http://localhost:8000/api/v1/status

# Update the status
curl -X POST -H "Content-Type: application/json" -d '{"status": "not OK"}' http://localhost:8000/api/v1/status

# Build the Docker image
docker build -t http-server .

# Run the Docker container
docker run -p 8000:8000 http-server