# Create Docker Image
>Do modification in base image :

    > Make Empty Directory and go there...
    > make file like index.html
    > make a file "Dockerfile" (D must be in Capital)
    > open Dockerfile and write
        
        FROM    fedora
        // This is base image where we want some changes
        // From check images in local system. If not present then pull it from dockerhub

        MAINTAINER xyz@gmail.com 
        // (optional : info about image creater)  

        RUN yum install httpd -y
        // launch a container and do the changes

        COPY index.html /var/www/html
        // source is base os --> container

        EXPOSE 80
        // EXPOSE 8080 for tomcat
        // We want to use http protocol inside container
        // To use https , use port number 443

        //  NOTE :  Container doesn't support Systemctl(Systemd : Parent process of redhat) command becoz it runs only one process.
                # kill -s STOP `pidof firefox`        
                # kill -s CONT `pidof firefox`

        ENTRYPOINT httpd -DFOREGROUND   (Cannot replace command that we want to run at startup of our container)
                    OR 
        CMD  httpd -DFOREGROUND         (Can replace command at startup of container)
        // alternative way of starting httpd service
        // command that you want to run on startup of your container
        

>To Save Image :

    docker build -t "anyname" . 
                or
    docker build -t "anyname" /myweb 
    // (-t : tag , used to give name)
    // ( . or /myweb is location of file)

>Run image :

    docker run -it adhocweb 
            or
    docker run -itd --name cc adhocweb (container will run in background)
            or
    docker run -itd --name web1 -p 1234:80 adhocweb

    // run 50 docker container
    import os
    for i in range(50):
        os.system(docker run -itd fedora bash)
