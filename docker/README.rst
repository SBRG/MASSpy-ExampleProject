Directory for files needed to build Docker containers.

To build the image from the MASSpy-ExampleProject repository:

docker build -t sbrg/masspy-exampleproject -f ./docker/Dockerfile ./

To build the container from the image:

docker run --rm \
    --mount type=volume,src=mass_project,dst=/home/masspy_user/mass_project/ \
    --publish 8888:8888 \
    -it sbrg/masspy-exampleproject
