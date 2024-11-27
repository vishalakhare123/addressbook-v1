pipeline {
    agent any

    stages {
        stage('Compile') {
            steps {
                script{
                    echo "Compiling the code"
                }
                
            }
            
        }
        stage('CodeReview') {
            steps {
                script{
                    echo "Code Review Using pmd plugin"
                }
                
            }
            
        }
         stage('UnitTest') {
            steps {
                script{
                    echo "UnitTest in junit"
                }
                
            }
            
        }
        stage('CodeCoverage') {
            steps {
                script{
                    echo "Code Coverage by jacoco"
                }
                
            }
            
        }
        stage('Package') {
            steps {
                script{
                    echo "packaging the code"
                }
                
            }
            
        }
    }
}
