pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M3"
    }

    stages {
        stage('Example') {
            steps {
                echo 'Hello, Maven'
                bat 'mvn --version'
                //sh 'mvn --version'
            }
        }
        stage('clone') {
            steps {
                // Get some code from a GitHub repository
                git branch: 'dev', url: 'https://github.com/Srishty1501/Jenkins_Demo.git'
            }

            
        }
        stage ('Build') {
            steps {
                bat 'mvn clean install' 
            }
            post {
                success {
                    junit 'target/surefire-reports/**/*.xml' 
                }
            }
        }
    }
}
