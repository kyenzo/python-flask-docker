node {

    stage("Git Clone"){

        git credentialsId: 'GIT_HUB_CREDENTIALS', url: 'https://github.com/kyenzo/python-flask-docker.git'
    }
    
    stage("Run tests"){
        echo 'Unit tests...'
    }
    
    stage("Remove Previous Container"){
        sh 'sudo docker rm -f my-app'
    }

    stage("Build Docker Image"){
        sh 'sudo docker version'
        sh 'sudo docker build -t python-flask-docker .'
        sh 'sudo docker image list'
        sh 'sudo docker tag python-flask-docker kyenzo/python-flask-docker:python-flask-docker'
    } 
    
    stage("Run App Container"){
        sh 'docker run --name my-app -d -p 8787:8787 kyenzo/python-flask-docker:python-flask-docker'
    }
}
