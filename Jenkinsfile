pipeline{
    agent any
    tools {
        maven 'Maven'
    }
    stages{
        stage("test"){
            steps{
                bat 'mvn test'
            }
            
        }
        stage("build"){
            steps{
                bat 'mvn package'
            }
            
        }
         stage('Archive') {
            steps {
                // Archive the generated WAR file
                archiveArtifacts artifacts: '**/target/*.war', allowEmptyArchive: true
                stash includes: '**/target/*.war', name: 'war-artifact'
            }
        }
        stage("deploy"){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'deployTest', path: '', url: 'http://localhost:9494/')], contextPath: 'calculatorApp', war: '**/*.war'
            }
            
        }
        
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
