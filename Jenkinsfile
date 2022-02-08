pipeline {
    agent any
     environment {
        Maven= "C:\\Users\\MONICA-MARY-HOWELL\\Documents\\apache-maven-3.8.4\\bin"
    }
    stages {
        stage("SCM Checkout") {
            steps {
                git 'https://github.com/Sylvagit/SpringBoot-Rest-Swagger-App.git'
            }
        stage("Build") {
            steps {
                bat 'mvn clean compile package'
            }
        stage("Deploy") {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcatid', path: '', url: 'http://localhost:8080/')], contextPath: 'Springboot', onFailure: false, war: '**/*.war'
            }
            post {
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
    }
  }
}
}
