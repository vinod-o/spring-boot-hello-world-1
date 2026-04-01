pipeline{
    agent any
    stages{
        stage('checkout'){
            steps{
                echo 'checkout code from github'
                git branch: 'main', url: 'https://github.com/vinod-o/spring-boot-hello-world-1.git'
            }
        }
        stage('build'){
            steps{
                echo 'Build the application'
            }
        }
    }
}