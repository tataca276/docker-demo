pipeline {
    
    agent any
/*    environment{	
		  //  credentialsId: artifactory	
   }*/	    

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
	    stage("Artifactory configuration"){
		steps{
		    rtserver ( 
			id: "Art-Server"
			
		    )    
		}
	    }
	stage("Docker push") {
     	     steps {
	 	script{
  	    	    docker.build("bootcampyyz-bootcampdockerhub.jfrog.io/artifactory/bootcampdockerhub/bootcampapp:v1")
		}
	     
	        rtDockerPush(
	            serverId: "Art-Server",
	            image: "bootcampyyz-bootcampdockerhub.jfrog.io/artifactory/bootcampdockerhub/bootcampapp:v1",
	            targetRepo: 'https://bootcampyyz.jfrog.io/artifactory/bootcampdockerhub'
		
	        )
	     }     
	}
     }
}
