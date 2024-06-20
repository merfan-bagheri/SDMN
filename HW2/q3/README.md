# Problem 3 (Docker) 20 points
This problem is about Docker. In this problem you write a simple HTTP server and dockerize it. You
can use your language of choice for this problem.
Your HTTP server has only one endpoint: /api/v1/status. This endpoint must handle GET and
POST HTTP methods. When the request method is GET, the server sends this JSON response:
{ "status": "OK" }
with status code 200. When the request method is POST with a body like this:
{ "status": "not OK" }
The server returns the body:
{ "status": "not OK" }
with status code 201. From now on every other GET request is responded with "not OK" status until
another POST request changes it to something else. Your server listens on port 8000.
After implementing the web server, write a Dockerfile and build an image for your server. You
should be able to create a container from that image and publish its port on your host.
Deliverables:
• The code of your HTTP server.
• A Dockerfile to build a docker image from your code.

# Build the Docker image
docker build -t http-server .

# Run the Docker container
docker run -p 8000:8000 http-server

# Get the current status
curl http://localhost:8000/api/v1/status

# Update the status
curl -X POST -H "Content-Type: application/json" -d '{"status": "not OK"}' http://localhost:8000/api/v1/status
