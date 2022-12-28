pipeline {
    agent any 
    stages {
        stage('Cloning Git') {    
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/saadmd29/Project-Lift-And-Shift.git']]])
            }
        }
        stage('BUILD') {    
            steps {
               sh 'mvn clean install -DskipTests'
            }
        }
        stage('pushing image to hub') { 
            steps {
               sh ' docker  login --username  saadmd29 --password "Azian@123" && docker push saadmd29/test:v1 ' 
            }
            post {
		    success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
        // Building Docker images
        stage('Building image') { 
            steps {
               script {
              dockerImage = docker.build "${IMAGE_REPO_NAME}:${IMAGE_TAG}"
            }
        }
        stage ('pushing image to hub') {
            steps {
            sh 'docker  login --username  saadmd29 --password "Azian@123" && docker push saadmd29/test:v1'
            }
        }
    }
}
