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
        stage("print"){
            steps{
                echo 'deploy'
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