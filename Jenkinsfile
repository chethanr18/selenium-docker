pipeline {
    // master executor should be set to 0
    agent any
    stages {
        stage('Build Jar') {
            steps {
                //sh
                bat "mvn clean package -DskipTests"
            }
        }
        stage('Build Image') {
            steps {
                //sh
                bat "docker build -t=chethanr18/selenium-docker ."
            }
        }
        stage('Push Image') {
            steps {
			    withCredentials([usernamePassword(credentialsId: 'chethanr18', passwordVariable: 'chethan-18', usernameVariable: 'chethanr18')]) {
                    //sh
			        bat "docker login --username=${usernameVariable} --password=${passwordVariable}"
			        bat "docker push chethanr18/selenium-docker:latest"
			    }                           
            }
        }
    }
}
