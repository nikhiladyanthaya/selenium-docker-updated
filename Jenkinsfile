pipeline {
    agent any
    stages {
        stage('Build Jar') {
            steps {
                    bat "mvn clean package -DskipTests"
            }
        }
        stage('Build Image') {
            steps {
                    bat "docker build -t=nikhiladyanthaya/selenium-docker:1.0 ."
            }
        }
        stage('Push Image') {
            steps {
  		   	 withCredentials([usernamePassword(credentialsId: 'DockerHub', passwordVariable: 'pass', usernameVariable: 'user')]) {
                    //sh
			        bat "docker login --username=${user} --password=${pass}"
			        bat "docker push nikhiladyanthaya/selenium-docker:1.0"
			    } 
  
  
             }
        }
    }
}
