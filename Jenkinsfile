
pipeline {
    agent any

    tools {
       
        maven 'Maven'
    }

    environment {
        SONAR_TOKEN = credentials('sonar-token')
    }

    stages {

        stage('Checkout') {
            steps {
                git(
                    branch: 'main',
                    url: 'https://github.com/sakshiK5002/SonarProject.git'
                )
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

      
stage('SonarQube Code Analysis') {
    steps {
      
            sh '''
                mvn org.sonarsource.scanner.maven:sonar-maven-plugin:5.8.0.7211:sonar \
                  -Dsonar.projectKey=my-project \
                  -Dsonar.projectName=my-project \
                  -Dsonar.host.url=http://13.127.110.57:9000/ \
                  -Dsonar.token="$SONAR_TOKEN"
            '''
        
    }
}

    }
}
