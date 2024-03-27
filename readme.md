Docker and Python
For this assignment you will be combining Docker with Python to create a program that generates a QR code PNG file that contains a URL. The QR code can be viewed with the camera on your phone to allow a user to click on it and send them to the target website. You must make your program generate a QR code that takes someone to your GitHub homepage i.e. https://github.com/kaw393939

Setup
Goto Docker.com and Install docker - https://www.docker.com/get-started/
Signup for your own Docker account
Submission Requirements:
Add the QR code image that links to your own GitHub homepage that you generate to the readme.md file, so that it appears below.
PUT YOUR QR CODE IMAGE

Add an image of viewing the log of successfully creating the QR code below. PUT YOUR LOG IMAGE HERE
Lesson Video
Scaling and Backend Software Engineering
Docker and Cloud Computing Intro
Readings / Tutorials - No, really you should read these
Containerization vs. Virtualization
Official docker Getting Started - Go over all the sections
Entrypoint vs. CMD vs. RUN
Make QR with Python
Make Dockerfile
Args and Environment Variables in Docker
Building the Image
docker build -t my-qr-app .
This command builds a Docker image named my-qr-app from the Dockerfile in the current directory (.).

Running the Container with Default Settings
docker run -d --name qr-generator my-qr-app
Runs your QR code generator application in detached mode (-d) with a container named qr-generator.

Setting Environment Variables for QR Code Customization
docker run -d --name qr-generator \
  -e QR_DATA_URL='https://example.com' \
  -e QR_CODE_DIR='qr_codes' \
  -e QR_CODE_FILENAME='exampleQR.png' \
  -e FILL_COLOR='blue' \
  -e BACK_COLOR='yellow' \
  my-qr-app
Customizes the QR code generation settings through environment variables.

Sharing a Volume for QR Code Output
docker run -d --name qr-generator \
  -v /host/path/for/qr_codes:/app/qr_codes \
  my-qr-app
Mounts a host directory to the container for storing QR codes.

Combining Volume Sharing and Environment Variables
docker run -d --name qr-generator \
  -e QR_CODE_DIR='qr_codes' \
  -e FILL_COLOR='blue' \
  -e BACK_COLOR='yellow' \
  -v /host/path/for/qr_codes:/app/qr_codes \
  my-qr-app
A comprehensive command that configures the QR code settings and mounts volumes for QR codes.

Setting the arg for the url from the terminal
docker run -v .:/app qrcode --url htt/www.nobdoy.com
This is how you would set the url for the qr code

Basic Docker Commands Explained
Building an Image

docker build -t image_name .
Builds a Docker image with the tag image_name from the Dockerfile in the current directory.

Running a Container

docker run --name container_name image_name
Runs a container named container_name from image_name in the foreground / attached mode

docker run -d --name container_name image_name
Runs a container named container_name from image_name in detached mode

Listing Running Containers

docker ps
Shows a list of all running containers.

Stopping a Container

docker stop container_name
Removing a Container

docker rm container_name
Listing Docker Images

docker images
Lists all Docker images available on your machine.

Removing a Docker Image

docker rmi image_name
Removes a Docker image.

Viewing Logs of a Container

docker logs container_name
Displays the logs from a running or stopped container.

These commands cover the essentials of building, running, and managing Docker containers and images, along with specific examples for your QR code generation application.