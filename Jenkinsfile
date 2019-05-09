pipeline {
    agent any
    tools {maven 'localMAVEN'
        jdk 'localJDK'
    }
    stages{
        stage('Build'){
            steps {
                bat 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deploy To Staging'){
            steps {
                build job: 'Deploy-to-staging'
            }
        }
    }
}
