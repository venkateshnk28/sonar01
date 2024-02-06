pipeline {
    agent any
    
    environment {
        SONARQUBE_HOME = tool 'sonarqube01'
    }

    stages {
        stage('clone from github(GitHubBuild)') {
            steps {
                git branch: 'master', url: 'https://github.com/venkateshnk28/sonar01.git'
            }
        }

        stage('Maven Build') {
            steps {
                sh 'mvn clean install package'
            }
        }

        stage('SonarQube Analysis') {
            steps {
	    	withSonarQubeEnv('sonar') {
                        sh "${SONARQUBE_HOME}/bin/sonar-scanner -Dsonar.projectKey=EKART -dsonar.projectName=EKART -dsonar.java.binaries"
               
                }
            }
        }
    }
}


