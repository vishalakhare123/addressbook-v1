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
                   echo "Compiling in ${params.Env}"
                              
                
            }
            
        }
        stage('CodeReview') {
            steps {
                        echo 'Code Review Using pmd plugin'
                    
                }
                
            }
            
        
         stage('UnitTest') {
                when{
                expression{
                    params.executeTests == true
                }
            }
            steps {
                
                    echo 'testing the code with junit'
                                    }
                
            }
            
         
        stage('CodeCoverage') {
            steps {
                
                    echo 'Code Coverage by jacoco'
                    
                }
                
            }
            
        
        stage('Package') {
             steps {
                    echo "packing the version ${params.APPVERSION}"
                }
            }

            stage('publish') {
                input{
                message "Select the platform for deployment"
                ok "Platform Selected"
                parameters{
                    choice(name:'Platform',choices:['EKS','EC2','On-prem'])
                }
            }
            steps {
                
                    echo 'publish the artifact to jfrog'
                    
                }
                
            }
            
    }
}
