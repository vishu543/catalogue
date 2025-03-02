pipeline {
    agent any
    parameters{
        choice(name: 'action', choices: ['apply', 'destroy'], description: 'pick the apply or destroy option')
    }
    environment{
        packageversion = ' '
    }
    stages{
        stage("Terraform init"){
            steps{
                sh """
                    Terraform init
                """
            }
        }
    
    
        stage(" package version"){
            steps{
                script{
                    def packageJson = readJSON file: 'package json'
                    packageversion = packageJson.version
                }
            }
        
    }
    
        stage("deploy"){
            when{
                expression{
                    params.action = 'apply'
                }
            }
            input{
                message "should we continue"
                ok "please continue"
            }
            steps{
                echo " application is deployed"
            }
        
        }
    }
}