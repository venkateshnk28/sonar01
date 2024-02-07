pipeline {
    agent any

   stages {
        stage('clone from github(GitHubBuild)') {
            steps {
                git branch: 'master', url: 'https://github.com/venkateshnk28/sonar01.git'
            }
        }
        stage('build war file(MavenBuild)') {
            steps {
                sh "mvn clean install package"
            }
        }
        stage('deploy to tomcat(DeployBuild)') {
            steps {
                sh "sudo scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/tomcat/webapp/target/webapp.war root@34.226.214.58:/home/ec2-user/tomcat/webapps/"
            }
        }
    }
}



