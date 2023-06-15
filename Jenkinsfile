pipeline {
    agent any

    stages {
        stage ('Docker Build') {
            steps {
                script {
                    sh 'sudo docker build -t fabio-brief14 .'
                    echo 'Build Image Completed'
                }    
            }
        }

        stage ('Docker Tag') {
            steps {
                script {
                    sh 'sudo docker tag fabio-tp-game fabiomp/fabio-brief14'
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
                    sh 'sudo docker push fabiomp/fabio-brief14'        
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
                        remote.password = '****'
                        remote.allowAnyHosts = true
                        stage('Remote SSH') {
                            sshCommand remote: remote, command: "sudo docker pull fabiomp/fabio-brief14"
                            sshCommand remote: remote, command: "sudo docker run -d -p 1234 --name tondocker fabiomp/fabio-brief13"
                            
        
                        }
                    }
                }
            }
        }
    }
}
