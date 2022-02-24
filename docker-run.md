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
	  		
### RUN Command : Optional features

Purpose | Switch Syntax | Example
-------|---------------|-----------
Interactive Mode  | -it | docker run -it ubuntu sh
Detached Mode | -d  | docker run -d tomcat:8
Container Name | --name [NAME] | docker run -d --name t1 tomcat:8
Port Forwarding | -p [HostPort]:[GuestPort] | docker run --name t1 -d -p 9000:8080 tomcat:9 
Volume Binding | -v [HostPath]:[GuestPath] | docker run -d --name t2 -v $PWD/myapp:/usr/local/tomcat/webapps/ -p 9000:8080 tomcat:8

### Demo with Volume and Port Forwarding

1.	Verify no other container running

	```
	docker stop $(docker ps -q)
	docker container prune -f
	```

2.	Create a new folder `myapp` with `index.html` page inside

	```
	mkdir myapp
	cd myapp
	nano index.html 
	```
3.	Inside the `nano` editor add following lines (Sample HTML).

	```html
	!DOCTYPE html>
	<html>
	<head>
	<style type="text/css">
	body{
	margin: 0px;
	padding: 0px;
	}
	h1, p {
	margin: 0px;
	padding: 10px;
	}
	h1{
	background-color: lightblue ;
	}


	</style>
	<title>Home Page</title>
	<h1>The Solar System</h1>
	<p>The quick brown fox jumps over the lazy dog. The quick brown fox jumps over the lazy dog.The quick brown fox jumps over the lazy dog.
	</html>
	```

4.	Use keyboard shortcut `CTRL+X` to save and close the nano editor, you have to press `Y` when it ask for writing changes.

5.	Go back to previous directory and then launch a new container.

	```
	cd ..
	docker run --name t1 -d -p 9000:8080 -v $PWD/myapp:/usr/local/tomcat/webapps/ROOT/ tomcat:8
	```

6.	Start firefox web-browser with `localhost:9000`

	```
	firefox http://localhost:9000
	```

7.	Try making few changes to myapp/index.html and refresh browser window.
