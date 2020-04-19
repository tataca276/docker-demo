pipeline {
    
    agent any
    environment{	
		  //  credentialsId: artifactory	
   }	    

    stages {
	stage("Checkout"){
	    steps{
		git url: 'https://github.com/tataca276/docker-demo.git'
	    }
	}
/*        stage('Test') {
 	    agent { dockerfile true }
            steps {
                sh 'node --version'
                
            }
        }
*/	    
	stage("Docker push") {
     steps {
	script{
			rtserver = Artifactory.server "Art-Server"
	    rtDocker = Artifactory.docker server: rtserver

  	    docker.build("bootcampyyz-bootcampdockerhub.jfrog.io/artifactory/bootcampdockerhub/bootcampapp:v1")
		rtDocker.push 'https://bootcampyyz-bootcampdockerhub.jfrog.io/artifactory/bootcampdockerhub/bootcampapp:v1', 'https://bootcampyyz.jfrog.io/artifactory/bootcampdockerhub'
	}
     }
}
    }
}
