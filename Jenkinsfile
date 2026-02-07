pipeline {
    agent any

    tools {
    maven 'maven'
    jdk 'jdk-21'
}


    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: '<your-git-repo-url>'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [
                    tomcat9(
                        credentialsId: 'tomcat-creds',
                        path: '',
                        url: 'http://localhost:8080'
                    )
                ],
                contextPath: 'my-webapp',
                war: 'target/my-webapp.war'
            }
        }
    }
}
