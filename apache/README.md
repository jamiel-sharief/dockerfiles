# Apache Docker Container

Includes Apache, PHP,PHP cli, PHP unit, Composer and number of common PHP extensions.

Run these commands from within the apache folder.

1. Build the image
`docker build -t apache .`

2. Start the container
`docker run -p 80:80 --name apache -d apache`

You can check its running by `docker ps`

3. execute command within
`docker exec -it apache bash`
