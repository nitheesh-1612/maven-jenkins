pipeline {
    agent any
  
    stages {
        stage {
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo "Archiving the artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deploy to tomcat Server') {
            steps {
                deploy adapters: [tomcat9(credentialsId: '19f47c16-98f9-4f92-a0d6-004bb9ee6290', path: '', url: 'http://35.185.232.230:8080/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
