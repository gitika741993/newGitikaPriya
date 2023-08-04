pipeline {
    agent any

    stages {
        stage('GitPipeline') {
            steps {
                git credentialsId: 'Git', url: 'https://github.com/gitika741993/newGitikaPriya.git'
            }
        }
        stage("build & SonarQube analysis") {
            agent any
            steps {
              withSonarQubeEnv('My SonarQube Server') {
                sh 'mvn clean package sonar:sonar'
              }
            }
          }
          stage("Quality Gate") {
            steps {
              timeout(time: 1, unit: 'HOURS') {
                waitForQualityGate abortPipeline: true
              }
            }
          }
        
    }
}

