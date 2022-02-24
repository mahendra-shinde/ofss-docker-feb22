Container Images

- An 'Image' is the immutable template using which, you may create any number of instances / containers.
- An Image cannot be modified, but can be EXTENDED into another image with changes !
- Image is MADE-UP of few layers (No Max limit ! but fewer is better). "Layers" are shared between mutliple images.
- In Docker, each Layer is assigned a Global Unique ID (Which actually is a Thumprint calculated using SHA256)

Container Instance
- Objects created from an Image / Container Image.
- An Image occupies just "storage" whereas 'instance' uses cpu, ram and network.
- Instance would use all the layers from the image, which are READ-ONLY.
- Each Container / Container-Instance is assigned a "Writable Layer" which acts as "ephermal storage" (Non persistent)
  - When container is DELETED, it will delete the writable layer with it !
  - For "persistent storage" use "Volumes"

Container Registry (Docker Registry)
- Remote server which contains lots of "repositories" of images.
- Each repository represents SINGLE application and it's VERSIONS
  - each version is represented by an image with tag
 
Example:
	Image name:	mahendrshinde/myweb:3, mahendrshinde/myweb:2
	Repository  >>  mahendrshinde/myweb
	Version/Tag >>  3, 2  
