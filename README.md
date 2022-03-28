Task #1
-------
1. Started with versioning application zip by pushing to new remote GitHub repo.

2. While creating docker files, ensured right order to minimize docker build time - depdendent package installations, copy project, build/test and entrypoint. Also added .dockerignore for to avoid loading all the files in current dir to daemon and avoid copying into docker build. Used yarn instead of npm, as it does parallel downloads of packages (yarn is also recommended in readme ;) )

3. Generated python requirements.txt as it was missing using pipreqs package. "DevOps-Assignment\api > python -m pipreqs.pipreqs --encoding=utf8". Manually added latest gunicorn version into it.

4. Created a dockerfile for nginx, to act as forward & reverse proxy.

5. Created a docker-compose.yaml to better manage all the modules/microservices of the application, refering existing dockerfiles, adding dependency between services and exposing proxy server port.

6. I think at this point though react app was reachable, no data was populated in UI as App.js was pointing to URL http://localhost:5000/stats. This was because as api (on port 5000) wasn't exposed to browser as App.js was getting executed on my browser. So I've changed it to proxy URL http://localhost:30100/stats.

**On doing "docker-compose up --build" access app on - http://localhost:30100/**


Task #3:
--------
1. Next instead of doing task #2, I thought may be it is a good idea to task#3 as task#3's output can be better leveraged in task#2

2. Tried to generate kubernetes service files using docker-compose using a tool called kompose, but tool was throwing errors related to the format of the file, though it was all good. As couldn't got any good resolution for the problem on internet, handcrafcted deployment and service kubernetes resources for each docker service using Lens IDE, as it is having resource templates to build up on.

3. As kubernetes pods need docker images, in docker compose added directives for images to be pushed to docker-hub registry on build.

4. Tried enabling ingress-controller on minikube and defining ingress, but for some unknown reason, ingress-controller couldn't obtain external IP. So had to workaround by defining a port forward rule from proxy server internal service to my local system as in kubernetes/README.md file

**Access app on : http://localhost:30100/**

Task #2
-------
1. In Azure cloud created a kubernetes cluster and a container registry.
2. Added deployments and services using yaml files that are used for kubernetes cluster used with minikube. Created ingress and defined rules to redirect based on path
3. Imported nginx ingress controller images to Azure cloud registry and installed the same via helm charts.

**app is available on public IP with https having self signed certificates: https://20.207.108.195/**