# Deploying your React App to Docker
##Step 1 - Install Docker
• Head over to ```https://docs.docker.com/docker-for-mac/install/```

• Click
`Download from Docker Hub`

• Create a login

• Click `get docker` 

• Once `Docker` is downloaded, drag it into the `Applications`

• You should see this icon appearing on the top right of your screen ![alt text](docker.png "Docker Logo")

``` 
// terminal
=> docker version

Client:
 Version:	18.03.0-ce
 API version:	1.37
 Go version:	go1.9.4
 Git commit:	0520e24
 Built:	Wed Mar 21 23:06:22 2018
 OS/Arch:	darwin/amd64
 Experimental:	false
 Orchestrator:	swarm

Server: Docker Engine - Community
 Engine:
  Version:	18.09.2
  API version:	1.39 (minimum version 1.12)
  Go version:	go1.10.6
  Git commit:	6247962
  Built:	Sun Feb 10 04:13:06 2019
  OS/Arch:	linux/amd64
  Experimental:	false
```
## Step 2 - Creating a Docker Image
• In same level as package.json `touch Dockerfile`

```
└── services
    ├── Dockerfile
    ├── app-directory
       ├── README.md
       ├── node_modules
       ├── package-lock.json
       ├── package.json
       ├── public
       ├── readme
       └── src
    
```

```
#Dockerfile

FROM node:11.9.0-alpine

ADD <app-directory> /opt/<directory-name>
WORKDIR /opt/<directory-name>

RUN npm install
RUN npm run build

EXPOSE 3000

CMD ["npm", "start"]
```

• You can then build the image by running: 
` docker build -t <your-docker-username>/<app-name> .`
(Don't forget the ".")

## Step 3 - Running Container
• An image is like a static container. 

• In order to run the container execute:
` docker run -p 3000:3000 <your-docker-username/<app-name>`

• Go to `0.0.0.0:3000` and it should be running

## Step 4 - Pushing/Pulling 
##### To push to docker hub

` docker push <your-docker-username>/<app-name> `

• You may need to docker login

#####To pull from hub
`docker pull <app-name>`