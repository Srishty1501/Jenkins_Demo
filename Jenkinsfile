pipeline {
    agent {
    label 'Slave1
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
