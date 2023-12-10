# Jenkins Crash Course

## # Angular Project deployed in this course
[Docker Crash Course - Github Repo](https://github.com/packetcode/docker-crash-course)

## # Install Docker
[Install Docker on Windows - Official Documentation](https://docs.docker.com/desktop/install/windows-install/)

## # Install Jenkins in Docker

#### Build Jenkins Image
``` bash
docker build -t jenkins-jdk17:1.0 .
```

#### Connect local daemon to docker image and start the container
``` bash
docker run -p 8080:8080 -p 50000:50000 -d --name jenkins-docker -v /var/run/docker.sock:/var/run/docker.sock -v jenkins_home:/var/jenkins_home jenkins-jdk17:1.0
```

## # Install Node Js

#### Install nvm
``` bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
```

#### Load nvm
``` bash
export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
```

#### Install and use node 16 (Linked angular project needs node 16 specifically)
```
nvm use 16
```

## # Building Freestyle Project

#### Shell command
``` bash
docker image build -t angular-app-docker:1.0 .
```

## # Building Pipeline Project

#### Complete Jenkins Pipeline Script
[Jenkins File - Pipeline Script](./Jenkinsfile)
