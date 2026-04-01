pipeline{
    agent any
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
                sh "mvn clean compile  "
            }
        }
        stage('SonarQubeAnalysis'){
            steps{
                withSonarQubeEnv("${SONAR_SERVER}") {
                    sh """
                        mvn sonar:sonar \
                        -Dsonar.host.url=http://52.91.111.127:9000 \
                        -Dsonar.login=$SONAR_AUTH_TOKEN
                        """
                     
                }
            }
        }
        stage('Quality Gate'){
            steps{
                timeout(time: 2, unit:'MINUTES'){
                    waitForQualityGate abortPipeline: true
                }
            }
        }
        stage("build the maven code"){
            steps{
                sh 'mvn clean install'
            }
        }
    }
}