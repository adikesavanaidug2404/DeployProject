pipeline {
    agent any

    stages {
        stage('clone from github(GitHubBuild)') {
            steps {
                git branch: 'master', url: 'https://github.com/adikesavanaidug2404/DeployProject.git'
            }
        }
        stage('build war file(MavenBuild)') {
            steps {
                sh "mvn clean install package"
            }
        }
        stage('deploy to tomcat(DeployBuild)') {
            steps {
                sh "sudo scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/deploy/webapp/target/webapp.war root@34.207.242.242:/home/ec2-user/tomcat/webapps/"
            }
        }
    }
}
