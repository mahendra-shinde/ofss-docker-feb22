# What & Why Containers


Application has "dependencies" like

- Language runtime
- Third Party Libraries
- Server Runtime (Microsoft IIS, Apache HTTPD/Tomcat, GlassFish, WebLogic, NGINX )
- OS Shell 

When "Application" is built and READY for deployment, 
Traditional approach:  Developer would just "SHARE" the application binary (dll, exe, jar/war...) with Other stages.
Modern approach     :  Developer should "SHARE" not just application binary but, the entire stack of dependencies.

## What is Container ?
- Generic Wrapper for Application and ALL the dependencies of application.
- Enables easy "Ship" and "Deploy" of application.
- Container use "Host OS Kernel", Linux Container cannot run on Windows OS and Windows Container wont run on Linux OS

### Alternate Option: Virtual Machine
- VM is much more bigger is size relative to container
- VM always contain a full OS (Guest OS)				
- Guest OS inside VM can be different than the Host OS
- One Container is for ONE SINGLE application, where as One VM may carry multiple applications.
- In Containers, all system resources (CPU, RAM & Network) are exclusive for Application,
	In VM, all these system resources are SHARED between Guest OS and Application(s) inside.
