Docker sample for CS347
Jeff Ondich
Last updated 30 April 2025

This directory contains a Dockerfile and a Flask app. The goal
is to illustrate how to create and launch a Docker container
running the back end of a web application.

I'm using Flask in this sample because:
- None of you are using Flask for your projects, so I'm not
doing all of your docker setup for you.
- I have Flask samples lying around from teaching CS257.

This is how I have successfully tested this directory on a remote server. First,
login to the server where docker is running. Then:

    git clone https://github.com/ondich/cs347-2025-spring.git
    cd cs347-2025-spring/docker

Now, build an image based on this sample:

    docker build -t flask-demo --rm .
    docker images
        to check to make sure the flask-demo image got built

This image generates a container that launches the Flask app listening on
port 5000 inside the container. You now launch that container with a port
of your choosing on the remote server  like so:

Next, run a container, mapping the chosen port (I'm using 8888 here) on your server
to the port 5000 inside the container:

    docker run --rm --detach -p 8888:5000 flask-demo

Now, you should be able to hit your server with a browser

    http://SERVER_IP:8888/

to see the Flask application at work.

