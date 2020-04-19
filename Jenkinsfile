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
	    
	stage('Artifactory Config'){
	    steps{
	        rtserver(
		    id: "Art-Servre"
		    url: "https://bootcampyyz.jfrog.io/artifactory/bootcamp-repo/"
		    credentialsId: artifactory
		)	
	    }		
	}	    
	stage("Docker push") {
     steps {
   
	sh "docker push bootcampyyz-bootcampdockerhub.jfrog.io/artifactory/bootcamp-repo"
     }
}
    }
}
