pipeline {
    
    agent any
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
	stage('Artifactory Config'){
	    steps{
	        rtserver(
		    id: "Art-Servre"
		    url: "https://bootcampyyz.jfrog.io/artifactory/bootcampdockerhub/"
		    credentialsId: artifactory
		)	
	    }		
	}	    
	stage("Docker push") {
     steps {
  	def testImg = docker.build("bootcampyyz-bootcampdockerhub.jfrog.io/artifactory/bootcampdockerhub/bootcampapp:v1");
	rtserver.push("https://bootcampyyz-bootcampdockerhub.jfrog.io/artifactory/bootcampdockerhub/bootcampapp:v1", "https://bootcampyyz.jfrog.io/artifactory/bootcampdockerhub")
     }
}
    }
}
