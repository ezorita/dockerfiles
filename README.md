# Dockerfiles
The following docker files generate ubuntu images with some software and one sudo user.
## Ubuntu Xenial (16.04)
To build this docker image, use:

`docker build -t <image tag name> --build-args user=[user] -f Dockerfile_xenial .`

If `--build-args user=<username>` is not set, the image will have a sudo user `user`. The default password for the user is _docker_ and must be changed upon login.
This image comes with the following packages:
* sudo
* bash-completion
* emacs24-nox
* vim
* git
* python3
* python3-dev
* make
* r-base
* wget

To log into the machine, first create a docker container:

`docker run -it --name <cont name> <image tag name>`

then Ctrl+D to exit the interactive session. Start the container with:

`docker start <cont name>`

and then login using:

`docker exec -it <cont name> python -c "import pty; pty.spawn(('/bin/login',))"`
