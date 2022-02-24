# DOCKER CREATE / RUN

## What happens when you CREATE new container ?

- Verify the command and arguments, raise an error if any.
- Verify if IMAGE is available locally, 
	If YES, then check if local image is SAME as remote registry (source) image
		If YES, then Use local Image
		If NO, then DOWNLOAD the Updated Image
	If NO, then Download the image from source (remote registry).

> When you want to "pre-fetch" container, you should CREATE.

## Execution modes

1. Default : 

	Terminal mode, Container will produce the `Output` via Standard Output Stream (stdout)
	There would be NO "Standard Input" / does not accept any input.
	  
	
		example: 
			docker run hello-world 
			docker run -t hello-world
		

2. Interactive : 
	
	Container will product `Output` via Standard Output Stream (stdout)
	
	Will also ACCEPT the `Input` via "STDIN"

		example:
			docker run -it ubuntu sh
			docker run -ti ubuntu sh
			docker run -t -i ubuntu sh	   	

3. Detached / Daemon:
	
	Container will NOT have stdin and stdout. Use "docker logs" to check output
	
	Container will run in background.

	   example:
	   	docker run -d --name t1 tomcat:8
	   	docker logs t1
	  		
