# python-flask-docker
The repository contains:
1. Basic Python Flask app in Docker which prints the hostname and IP of the container
2. A Dockerfile to dockerize and run the application
3. A Jenkinsfile for the CI flow cofiguration

### Pre-requisites:
1. Windows 10+ OS
2. Java version 8 or 11 installed - https://jdk.java.net/java-se-ri/11 
3. Python installed on the host machine - https://www.python.org/downloads/
4. Docker Engine installed - https://docs.docker.com/desktop/windows/install/

### Clone the repository:
```
$ git clone https://github.com/lvthillo/python-flask-docker.git
```
### Install Jenkins locally:
1. Download the Jenkins client to your machine 
[Jenkins.war](https://get.jenkins.io/war/2.316/jenkins.war)
2. Open the terminal in the directory of the Jenkins client and run:
```
$ java -jar jenkins.war --httpPort=8383
```
3. Go to http://localhost:8383

### Create an Admin user for Jenkins:
1. Setup the 1 time password for Jenkins from the installation log
2. Example: bd389e2f59b040abaa45e2662514fb41
3. Create an admin user

### Add GitHub credentials to Jenkins:
1. In the Jenkins Dashboard - Go to Manage Jenkins > Manage Credentials
2. Click on the (Global) drop-down > Add Credentials
3. Set up the GitHub Username and Password
* The ID field is a placeholder for the password in the pipeline - 
Set to: GIT_HUB_CREDENTIALS
4. Save

### Setup the Pipeline to the Jenkinsfile:
1. In the Jenkins Dashboard - Click on New Item
2. Insert a name and choose Pipeline
3. Go to Pipeline section and choose Pipeline script from SCM, in the description
4. SCM = Git
5. Repository URL = https://github.com/kyenzo/python-flask-docker.git
6. Choose the credentials you've created

* Since the Jenkins cliend is installed locally - 
GitHub hook trigger for GITScm polling, is not possible.

### Run the Job and open the application on localhost:
1. Make sure that the Docker engine is running
2. Click build now
3. Go to http://localhost:8787

# The application is running!

### Original project repo and instrucations below:
```
$ git clone https://github.com/lvthillo/python-flask-docker.git
$ docker build -t lvthillo/python-flask-docker .
```

### Download precreated image
You can also just download the existing image from [DockerHub](https://hub.docker.com/r/lvthillo/python-flask-docker/).
```
docker pull lvthillo/python-flask-docker
```

### Run the container
Create a container from the image.
```
$ docker run --name my-container -d -p 8080:8080 lvthillo/python-flask-docker
```

Now visit http://localhost:8080
```
 The hostname of the container is 6095273a4e9b and its IP is 172.17.0.2. 
```

### Verify the running container
Verify by checking the container ip and hostname (ID):
```
$ docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' my-container
172.17.0.2
$ docker inspect -f '{{ .Config.Hostname }}' my-container
6095273a4e9b
```


