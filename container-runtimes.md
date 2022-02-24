# Container Runtimes 


- LXC & LXD (Older linux container runtimes)
- Docker (Runtime as well as Development tool)
- CRI-O  (Lightweight runtime, Not for development)
- LibcontainerD (Lightweight runtime, Internal Docker component)

## Docker As Container Development platform
- Popularized Containerization
- Application container platform (lxd & lxc were OS Container)
- With "Microsoft Partnership", introduced "Windows Container"
	- Windows Containers are supported only on
	  1. Windows 10 PRO / ENT
	  2. Windows Server 2016
	  3. Windows Server 2019
	  4. Windows Server 2022+
- Docker initiated Open source community "OCI" Open Container Initiative
  - Container images built with DOCKER can now run on any compatible container runtime.

## Docker Installations

1. Docker Community Edition (Docker CE)
	Free devtool available on linux.
	
2. Docker Enterprise Edition (Product from Mirantis )
	Licenced product, available for Windows & Linux.
	
3. Docker Desktop for Windows or MacOS
	Earlier Docker Desktop was part of "Community" or FREE Version
	Docker Desktop for "Individuals" is FREE, but for Organization it need licence.

### Few Sample commands:

```bash
docker version
docker info
```

### Docker Images 

Short name | Fully Qualified Name | Description
-----------|---------------------|-----------
mysql:5.7  | docker.io/library/mysql:5.7| Official Image on Docker hub
mahendrshinde/myweb:1 | docker.io/mahendrshinde/myweb:1 | User defined Image on docker-hub
`NA` |  container-registry.oracle.com/database/express:latest | Image from third party container registry (oracle), dont have short names.
		

> Official images on docker-hub doesn't include "docker-id"
	




	
