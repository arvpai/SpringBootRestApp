pipeline {
    agent any
        tools {
        gradle 'gradle_1'
    }
    stages {
        stage('Build') {
            steps {
              script {
                    try {
                        sh './gradlew clean build --no-daemon' //run a gradle build task
                    } finally {
                        echo "Build fails"
                    }
                }
            }
        }
      stage('Sonarqube code quality check') {
            steps {
                    withSonarQubeEnv(installationName :'sonar-9', credentialsId : 'jenkins-maven-poc') {
                    sh 'gradle sonarqube'
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
        stage('Compile') {
            steps {
                script {
                  try {
                        sh './gradlew clean test --no-daemon' //run a gradle task
                    } finally {
                        junit '**/build/test-results/test/*.xml' //make the junit test results available in any case (success & failure)
                    }
                }
            }
        }
     }
}
