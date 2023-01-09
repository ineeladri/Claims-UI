node {
      stage("Git Clone"){

        git branch: 'main', url: 'https://github.com/ineeladri/Claims-UI.git'
    }
   
    stage("Docker build"){
    sh 'docker build -t myapp:latest -f Dockerfile .'
        sh 'docker image ls'
    }
withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: 'test', usernameVariable: 'apurva09', passwordVariable: 'password']]) {
        sh 'docker login -u apurva09 -p $password'
	}
    stage("Pushing Image to Docker Hub"){
	     sh 'docker tag myapp apurva09/myapp:latest'
	   sh 'docker push apurva09/myapp:latest'
    }
}
