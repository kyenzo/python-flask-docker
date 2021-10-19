node {

    stage("Git Clone"){

        git credentialsId: 'GIT_HUB_CREDENTIALS', url: 'https://github.com/kyenzo/python-flask-docker.git'
    }
    
    stage("Run Unit tests"){
        echo 'Unit tests...'
    }
    
    stage("Build Docker Image"){
        bat 'docker version'
        bat 'docker build -t python-flask-docker .'
        bat 'docker image list'
        bat 'docker tag python-flask-docker kyenzo/python-flask-docker:python-flask-docker'
    } 
    
    stage("Run App Container"){
        bat 'docker run --name my-app -d -p 8787:8787 kyenzo/python-flask-docker:python-flask-docker'
    }
    
        stage("Run Integration tests"){
        echo 'Integration tests...'
    }
}
