sudo yum update -y
sudo amazon-linux-extras install docker
sudo service docker start
docker container ls/docker ps
docker container ls
docker ps
vi Dockerfile
docker build -t phpmyadmin:latest .
docker image ls
docker run -d --name first -p 82:80 phpmyadmin:latest
docker ps
docker exec --help
docker exec -it first bash
docker run -d -p 3306:3306 -e MYSQL_ROOT_PASSWORD=root MySQL(it should be there because if you directly launch from the MySQL image the container is going to be exited)
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version
If you encounter any login issue then check for the images and remove previous images then again try to login once again.

==========================================================================================================================================================================================

The docker system prune command is a shortcut that prunes images, containers, and networks. Volumes aren't pruned by default, and you must specify the --volumes flag for docker system prune to prune volumes. By default, you're prompted to continue. To bypass the prompt, use the -f or --force flag.
