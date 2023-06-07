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
        
        node {
            def remote = [:]
            remote.name = 'fabio'
            remote.host = '4.233.106.239'
            remote.user = 'fabio'
            remote.password = 'Dofus69200Fabio'
            remote.allowAnyHosts = true
                stage('Remote SSH') {
                    sshCommand remote: remote, command: "ls -lrt"
                    sshCommand remote: remote, command: "for i in {1..5}; do echo -n \"Loop \$i \"; date ; sleep 1; done"
                }
        }
    }
}
