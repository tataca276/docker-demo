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
	        def rtserver = Artifactory.server "Art-Server"
		def rtDocker = Artifactory.docker server: rtserver
		  //  credentialsId: artifactory
		)	
	    }		
	}	    
	stage("Docker push") {
     steps {
  	def testImg = docker.build("https://bootcampyyz-bootcampdockerhub.jfrog.io/artifactory/bootcampdockerhub/bootcampapp:v1");
	rtserver.push("https://bootcampyyz-bootcampdockerhub.jfrog.io/artifactory/bootcampdockerhub/bootcampapp:v1", "https://bootcampyyz.jfrog.io/artifactory/bootcampdockerhub")
     }
}
    }
}
