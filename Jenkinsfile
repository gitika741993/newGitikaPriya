pipeline {
    agent any

    stages {
        stage('GitPipeline') {
            steps {
                git credentialsId: 'Git', url: 'https://github.com/gitika741993/newGitikaPriya.git'
            }
        }
       stage('build && SonarQube analysis') {
            steps {
                withSonarQubeEnv('http://localhost:9000/') {
                    // Optionally use a Maven environment you've configured already
                    withMaven(maven:'Maven 3.5') {
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

