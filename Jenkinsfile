pipeline{
    agent any
    stages{
        stage("getting code") {
            steps {
                git url: 'https://github.com/ledjo31/VM-Monitoring-in-Azure.git', branch: 'main',
                credentialsId: 'github-credentials' //jenkins-github-creds
                sh "ls -ltr"
            }
        }
               stage("az login") {
            steps {                
                script {
                    echo "======== executing ========"
                    dir ("Terraform") {
                        sh "pwd"
                        sh "az upgrade --yes"
                        sh "az login"
                            }    }        
                        }
                    } 
       stage("Create the VM") {
            steps {                
                script {
                    echo "======== executing ========"
                    dir ("Terraform") {
                        sh "pwd"
                       /* sh "az upgrade --yes"
                        sh "az login"*/
                        sh "terraform init"
 /*                       sh "terraform apply --auto-approve --var-file=/var/jenkins_home/workspace/VM-Monitoring/Terraform/terraform.tfvars.json" */
                        sh "terraform apply --auto-approve
                         }    }        
                        }
                    } 
                stage("Ansible Playbooks") {
            steps {                
                script {
                    echo "======== executing ========"
                    dir ("ansible") {
                        sh "pwd"
                        sh "ansible-playbook  update-hosts.yml"
                        sh "ansible-playbook -i hosts install_prometheus.yml"
                        sh "ansible-playbook -i hosts install_grafana.yml"
                         }         }   
                        }
                    } 
                        stage("grafana playbook") {
            steps {                
                script {
                    echo "======== executing ========"
                    dir ("ansible") {
                        sh "pwd"
                        sh "ansible-playbook -i hosts install_grafana.yml"
                         }         }   
                        }
                    } 
                }
            post{
                success{
                    echo "======== Setting up infra executed successfully ========"
                }
                failure{
                    echo "======== Setting up infra execution failed ========"
                }
            }
             
        }          
   /* 
    post{
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }*/
<<<<<<< HEAD
=======
>>>>>>> 01cbca0 (Edit Jenkins file and main.tf)
>>>>>>> 72db0b3 (Edit Jenkins file and main.tf)
