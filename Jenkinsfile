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
                echo " init is implied"
            }
        }
    
    
        stage(" package version"){
            steps{
                script{
                    def packageJson = readJSON file: 'package.json'
                    packageVersion = packageJson.version
                    echo "$packageVersion"
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
        stage("destroy"){
            when{
                expression{
                    params.action = 'destroy'
                }
            }
            input{
                message "should we continue"
                ok "please continue"
            }
            steps{
                echo " application is destroyed"
            }
        
        }

    }
}