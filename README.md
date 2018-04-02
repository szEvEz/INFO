# Docker - How to cleanup resources
    
## [Cleanup docker volumes](https://github.com/chadoe/docker-cleanup-volumes)
    
    $ docker volume rm $(docker volume ls -qf dangling=true)
    $ docker volume ls -qf dangling=true | xargs -r docker volume rm
    
## Delete networks

    $ docker network ls  
    $ docker network ls | grep "bridge"   
    $ docker network rm $(docker network ls | grep "bridge" | awk '/ / { print $1 }')
    
## [How to remove old and unused docker containers](http://stackoverflow.com/questions/32723111/how-to-remove-old-and-unused-docker-images)

    $ docker ps
    $ docker ps -a
    $ docker rm $(docker ps -qa --no-trunc --filter "status=exited")

## [How to remove old and unused docker images](http://stackoverflow.com/questions/32723111/how-to-remove-old-and-unused-docker-images)
    
    $ docker images
    $ docker rmi $(docker images --filter "dangling=true" -q --no-trunc)
    
    $ docker images | grep "none"
    $ docker rmi $(docker images | grep "none" | awk '/ / { print $3 }')

## [Complete cleanup](https://www.digitalocean.com/community/tutorials/how-to-remove-docker-images-containers-and-volumes)

remove images, containers, volumes, and networks that are dangling

    $ docker system prune

to additionally remove any stopped containers and all unused images (not just dangling images)

    $ docker system prune -a