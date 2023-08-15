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
        stage('Build') {
            steps {
                // Clean and package the project using Maven
                dir('C:\\Users\\BISMILLAH\\Desktop\\Devops\\CalculatorApp') {
                    // Execute Maven commands
                    bat 'mvn clean package'
                }
            }
        }
         stage('Archive') {
            steps {
                // Archive the generated WAR file
                archiveArtifacts artifacts: 'C:\\Users\\BISMILLAH\\Desktop\\Devops\\CalculatorApp/target/*.war', allowEmptyArchive: true
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
