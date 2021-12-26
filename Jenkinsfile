pipeline{
    agent any
    stages {
	
      	stage('Checkout Code') 
			{
				steps 
				{
					echo 'Checkout the files from git repo-- Worked'
					checkout scm
				}
			}
		
		stage('Build') 
        {
            steps 
            {
            echo 'Build App'
			echo 'bat mvn clean install -- thi is for Windows'
			echo 'linux syntas mvn clean install'
			sh 'mvn clean install'
            }
        }
        stage('Build Docker Image') 
		{
            steps {
                script {
                  sh 'docker build -t repoj/my-app-web .'
			
                }
            }
        }
 stage('Push Docker Image'){
	  steps
	  {
       withCredentials([usernamePassword(credentialsId: 'uidpwd_method', passwordVariable: 'githubpassword', usernameVariable: 'githubuser')]) {
       sh "docker login -u ${githubuser} -p ${githubpassword}"
	       
	echo 'sh docker push devopshint/my-app-1.0--- didnt worked'
	sh 'docker image ls'
	sh 'docker push repoj/my-app-web'
      }
        
     }
	                     } 

	    
    }
}
