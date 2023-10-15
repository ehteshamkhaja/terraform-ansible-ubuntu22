pipeline {
    agent any
    stages {
      stage('Git clone into Jenkins workspace directory'){
       steps {
         sh 'git clone https://github.com/ehteshamkhaja/terraform-ansible-ubuntu22.git' 
      }
     }
    }
      stage('Terrform Init and Run terraform  Plan'){
       steps {
         dir('terraform') {
             sh 'terraform init && terraform plan'
          }
        }
      }

    stage('Provision VM using terraform') {
    steps{
      dir('terraform'){
      sh 'terraform apply --auto-approve'
     }
    }
    } 
   stage('Apply patches on the Provisioned VMs'){
 steps{
     sh 'ansible-playbook  -i /var/lib/jenkins/inventory/hosts ubuntu-22-patch/site.yml'
    }
    
    }
}
     
