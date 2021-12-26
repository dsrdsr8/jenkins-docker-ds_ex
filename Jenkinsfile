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
                  sh 'docker build -t devopshint/my-app-1.0 .'
                }
            }
        }
      stage('Push Docker Image'){
        withCredentials([string(credentialsId: 'Docker_Hub_Pwd_Fin', variable: 'Docker_Hub_Pwd_Fin')]) {
          sh "docker login -u dsrdsr8 -p ${Docker_Hub_Pwd_Fin}"
        }
        sh 'docker push devopshint/my-app-1.0'
     }
	    
    }
}
