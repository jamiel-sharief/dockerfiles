# OpenSSH Docker Container

1. Build the image
`docker build -t apache .`

2. Start the container
`docker run -p 22:22 --name mysql -d mysql`

You can check its running by `docker ps`

3. execute command within
`docker exec -it ssh bash`
