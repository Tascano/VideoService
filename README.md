# fantastic-lamp
Youtube, but simpler 

1. Build and Run the Docker Image
To build your image, navigate to the directory that has your Dockerfile and run the following command:
docker build -t video-processing-service .
The -t flag lets you tag your image so it's easier to find later.
List Docker images
docker images
Now, to run the image, use the docker run command:
docker run -p 3000:3000 -d video-processing-service
The -p flag redirects a public port to a private port inside the container. The -d flag runs the container in detached mode, leaving the container running in the background.

2. Test Converting a Local Video
Note: When we generate the image, ensure that there is still a raw video file in the root directory of the project.
Again, we can send a POST request to our /process-video endpoint using Thunder Client.

The request URL:

POST http://localhost:3000/process-video

The request body:

{
  "inputFilePath": "./nc-intro.mp4",
  "outputFilePath": "./processed-nc-intro.mp4"
}
To copy a file out of a running Docker container into your host, you can use the docker cp command. Here's how to do it:

docker cp <container-id-or-name>:/app/processed-nc-intro.mov ./
This command will copy the file from the container to the host system.

3. Clean Up
To list the running containers run:

> docker ps
To stop a running container run:

> docker stop <container-id-or-name>
To list all containers, even those that have been stopped, run:

> docker ps -a
To remove a container run:

> docker rm <container-id-or-name>