pipeline {
  agent any
  stages {
    stage('Build vote') {
          steps {
		sh 'cd vote'
		sh 'ls'
		sh 'cd vote'
		sh 'docker build -t 925528255726.dkr.ecr.ap-south-1.amazonaws.com/cloud_repo:v1_vote_1.0.0 .'
		sh 'docker push 925528255726.dkr.ecr.ap-south-1.amazonaws.com/cloud_repo:v1_vote_1.0.0'
		}
	}
    
    stage('Build result') {
      	  steps {
		sh 'cd ../result'
		sh 'docker build -t 925528255726.dkr.ecr.ap-south-1.amazonaws.com/cloud_repo:v1_result_1.0.0 .'
		sh 'docker push 925528255726.dkr.ecr.ap-south-1.amazonaws.com/cloud_repo:v1_result_1.0.0'
	       }
	} 
  
    stage('Build worker') {
      	  steps { 
		sh 'cd ../worker'
		sh 'docker build -t 925528255726.dkr.ecr.ap-south-1.amazonaws.com/cloud_repo:v1_worker_1.0.0 .'
		sh 'docker push 925528255726.dkr.ecr.ap-south-1.amazonaws.com/cloud_repo:v1_worker_1.0.0'
		}
	}

	stage('deploy'){
		steps{ 
		     sh 'docker stack deploy -c docker-stack.yml voting-app'
		     }
	}
   }
}
