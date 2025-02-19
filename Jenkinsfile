pipeline {
    agent none

    tools{
        maven "mymaven"
    }


       
    parameters{
        string(name:'Env',defaultValue:'Test',description:'environment to deploy')
        booleanParam(name:'executeTests',defaultValue: true,description:'decide to run tc')
        choice(name:'APPVERSION',choices:['1.1','1.2','1.3'])

    }
    

    stages {
        stage('Compile') {
            agent any
                       steps {
               script{
                   echo "Compiling in ${params.Env}"
                   sh "mvn compile"
                         
               }
                }
                
            }
            
        
        stage('CodeReview') {
            agent any
                   steps {
                    script{
                    echo "Code Review Using pmd plugin"
                    sh "mvn pmd:pmd"
                }
                     }
                
            }
            
       
         stage('UnitTest') {
            agent any
                when{
                expression{
                    params.executeTests == true
                }
            }
            steps {
                
                   script{
                    echo "UnitTest in junit"
                    sh "mvn test"
                }
                    
                }
                
            }
            
        stage('CodeCoverage') {
            agent {label 'node_1'}
            steps {
              
                   script{
                    echo "Code Coverage by jacoco"
                    sh "mvn verify"
                }

                    
                }
                
            }
            
        
        stage('Package') {
                  agent any
           steps {
                script{
                    echo "packing the version ${params.APPVERSION}"
                    sh "mvn package"
                }
                                   
                    
                }
                
            }
            
          stage('publish') {
            agent any
            input{
                message "Select the platform for deployment"
                ok "Platform Selected"
                parameters{
                    choice(name:'NEWAPP',choices:['EKS','EC2','On-prem'])
                }
            }
            steps {
                script{
                    echo "publish the artifact to jfrog"
                    sh "mvn -U deploy -s settings.xml"
                }

            }
    } 
}

}

