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
              withSonarQubeEnv(credentialsId: 'ae331794-4ae4-49bd-b717-4f50b45b6aa3', installationName: 'Sonar Server') {
    // some block
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

