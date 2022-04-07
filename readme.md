# Experimental Project
The project goals are to create a docker container for two services: frontend and backend. Each service has a developement and production environment. The developement environment allows to quickly develop by having the container mounting volume to the developer machine but otherwise everything is in the container (running code, node_modules, etc.). The production container contains all the transpiled JavaScript from TypeScript. Hot-reload enabled for frontend (SolidJS framework, but same with React CRA) and also with the backend (NodeJS).

# Documentations

## Docker References

### Multi-stage and target (FROM/AS)
https://www.docker.com/blog/speed-up-your-development-flow-with-these-dockerfile-best-practices/

### Docker Web App with Multi-Stage 
https://nickjanetakis.com/blog/best-practices-around-production-ready-web-apps-with-docker-compose
https://github.com/nickjj/docker-node-example/blob/main/Dockerfile

### Docker with a React Example (REACT CRA start and Nginx)
https://dev.to/karanpratapsingh/dockerize-your-react-app-4j2e
https://medium.com/geekculture/dockerizing-a-react-application-with-multi-stage-docker-build-4a5c6ca68166

### Docker with a Dev and Production setup
https://viralganatra.com/docker-nodejs-production-secure-best-practices/

### How to debug Docker build
https://stackoverflow.com/questions/26220957/how-can-i-inspect-the-file-system-of-a-failed-docker-build


# How to Debug Build

Run
```
 DOCKER_BUILDKIT=0 docker-compose build  
```
This will give some UUID for each step. Use the UUID for the step to debug with this command:

```
docker run -it <uuid> bash
```

If the build was successful, we can use the image name.

```
docker run -it backend:latest bash 
docker run -it frontend:latest bash 
```