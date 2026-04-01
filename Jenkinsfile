pipeline{
    agent any
    tools{
        sonarScanner 'SonarScanner'
    }
    environment{
        SONAR_SERVER = 'SonarQube'
    }
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
        stage('SonarQubeAnalysis'){
            steps{
                WithSonarQubeEnv("${SONAR_SERVER}") {
                    sh """
                        sonar-scanner \
                        -Dsonar.host.url = http://52.91.111.127:9000 \
                        -Dsonar.login = $SONAR_AUTH_TOKEN
                        """
                     
                }
            }
        }
    }
}