pipeline {
    agent any
        tools {
        gradle 'gradle_1'
    }
    stages {
        stage('Compile') {
            steps {
                gradlew('clean', 'classes')
            }
        }
        // stage('Long-running Verification') {
        //     environment {
        //         SONAR_LOGIN = credentials('jenkins-maven-poc')
        //     }
        // }
        // stage('Code Analysis') {
        //             steps {
        //                 gradlew('sonarqube')
        //             }
        //         }
            }
        }
