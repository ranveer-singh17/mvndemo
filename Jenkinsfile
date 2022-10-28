pipeline {
    agent any


    stages {
                 stage('Code Checkout') {
            steps {
                checkout([
                    $class: 'GitSCM', 
                    branches: [[name: '*/main']], 
                    userRemoteConfigs: [[url: 'https://github.com/ranveer-singh17/mvndemo.git']]
                ])
            }
        }
//         stage ('Build') {
//             when {
//                 branch 'main'
//             }
//             steps {
//                 bat 'javac test.java'
//                 bat 'test.java'
//             }
//         }
        stage('Testing'){
            steps{
                bat'echo running unit test cases'
            }
        }
        stage('Code_analysis'){
            steps{
                withSonarQubeEnv('SonarQube') {
                    bat 'mvn clean package sonar:sonar'
                }
            }
  }

                
            }
    post{
        always{
            mail to: "ranveersingh7600454082@gmail.com",
            subject: "Test Email",
            body: "Test"
        }
}
}
