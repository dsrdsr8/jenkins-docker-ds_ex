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
        stage('Deploy Docker Image') {
            steps {
                script {
                 withCredentials([string(credentialsId: 'docker-hub', variable: 'dockerHubPwd')]) {
                    sh 'docker login -u dsrdsr8 -p ${Rediffmail-1}'
                 }  
                 sh 'docker push devopshint/my-app-1.0'
                }
            }
        }
    }
}
