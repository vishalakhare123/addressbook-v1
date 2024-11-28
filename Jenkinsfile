pipeline {
    agent any
    
    parameters{
        string(name:'Env',defaultValue:'Test',description:'environment to deploy')
        booleanParam(name:'executeTests',defaultValue: true,description:'decide to run tc')
        choice(name:'APPVERSION',choices:['1.1','1.2','1.3'])

    }

    stages {
        stage('Compile') {
            steps {
                script{
                    echo "Compiling the code"
                   echo "Compileing in ${params.Env}"
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
                    echo "packing the version ${params.APPVERSION}"
                }
                
            }
            
        }
    }
}
