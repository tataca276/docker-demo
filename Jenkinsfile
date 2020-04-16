pipeline {
    agent any
    stages {
	stage("Checkout"){
	    steps{
		git url: 'https://github.com/tataca276/docker-demo.git'
	    }
	}
        stage('Test') {
 	    agent { dockerfile true }
            steps {
                sh 'node --version'
                
            }
        }
	    
	stage("Docker push") {
     steps {
   
	sh "docker push https://bootcampyyz.jfrog.io/artifactory/bootcamp-repo:latest"
     }
}
    }
}
