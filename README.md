# SharePoint Framework Office PNP Docker file

Docker images recipe for running [SharePoint Framework Pattern and Practices samples](https://github.com/SharePoint/sp-dev-fx-webparts).  


## Usage

- In the HOSTS file on your host add:
```
127.0.0.1    spfx
```
- Clone this repository
```
git clone https://github.com/StfBauer/docker-spfx-pnp-samples.git
```

- Create docker image specific to one of the sample listed on [SPFX PnP Samples](https://github.com/SharePoint/sp-dev-fx-webparts/tree/master/samples)  
For example create container for jquery-cdn sample pass in the following command: 
```  
docker build -t spfx-samples:jquery-cdn . --build-arg samplename="jquery-cdn"  
```  
Pass in folder name to image name and tag 'spfx-samples:<SPFX PnP Sample Foldername>'.  
Set 'samplename' build argument to same folder name.
- To run container  
```  
docker run -h spfx --name spfx-jquery-cdn -it -p 5432:5432 -p 4321:4321 -p 35729:35729 spfx-samples:jquery-cdn
```
Set ```--name``` argument to your desired name. In this case ```spfx-jquery-cdn``` was used.  
To exit container press ```CTRL+C``` this will exit the container.
- To restart container again:  
```
docker start spfx-jquery-cdn
```
- To access running container via shell  
```
docker exec -it spfx-jquery-cdn /bin/bash
```


## Known issues
There are some know issues on Windows documented on [Dockers Github page](https://github.com/docker/kitematic/wiki/Common-Issues-and-Fixes#windows-10).

## Limitations
Windows 10 Anniversary Update and Windows Server 2016 have native support for containers. At this moment Windows supports only containers built on Windows Server Core or Nano Server and you won't be able to run this container natively on Windows. Instead you should use Docker for Windows or Docker Toolbox.
