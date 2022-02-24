# Common docker commands

Purpose| Command | Example
-------|------|----------
List All Running Containers | docker ps | docker ps
List All Container (Including STOPPED) | docker ps -a | docker ps -a
Read/Show Manfiest/Metadata of Container | docker inspect [NAME] | docker inspect t1
System Resource Usage by All containers  | docker stats | docker stats
Get Inside Container (debugging) | docker exec -it [NAME] [SHELL] | docker exec -it t1 sh
Copy files from Host directory | docker cp [files] [Name]:[Path] | docker cp myapp/index.html t1:/usr/local/tomcat/ROOT/index.html
