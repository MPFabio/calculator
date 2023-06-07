pipeline {
    agent any

    stages {
        stage ('Docker Build') {
            steps {
                script {
                    sh 'sudo docker build -t fabio-tp-game .'
                    echo 'Build Image Completed'
                }    
            }
        }

        stage ('Docker Tag') {
            steps {
                script {
                    sh 'sudo docker tag fabio-tp-game fabiomp/fabio-tp-game'
                }
            }
        }

        stage('Docker Login') {
            steps {
                script {
                    sh 'sudo docker login -u fabiomp -p Aucunmdp69' 
                }    
            }
        }

        stage ('Docker Push') {
            steps {
                script {
                    sh 'sudo docker push fabiomp/fabio-tp-game'        
                }    
            }
        }    
        
        
        stage('SSH') {
            steps {
                script{
                    node {
                        def remote = [:]
                        remote.name = 'fabio'
                        remote.host = '4.233.106.239'
                        remote.user = 'fabio'
                        remote.password = 'Dofus69200Fabio'
                        remote.allowAnyHosts = true
                        stage('Remote SSH') {
                            sshCommand remote: remote, command: "sudo docker pull fabiomp/fabio-tp-game"
                            sshCommand remote: remote, command: "sudo docker run -d -p 5003:3000 --name calculator-key fabiomp/fabio-tp-game"
                            
        azureCLI commands: [[exportVariablesString: '', script: 'az group create --name FabioGrpRsrc --location westeurope'], [exportVariablesString: '/publicIpAddress|PUBLIC_IP', script: 'az vm create -n Fabio-AZ-Jenkins -g FabioGrpRsrc --image UbuntuLTS --data-disk-sizes-gb 10 20']], principalCredentialId: '7349d3b2-951f-41be-877e-d8ccd9f3e73c'
                        }
                    }
                }
            }
        }
    }
}
