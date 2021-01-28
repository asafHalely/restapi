pipeline {
    agent {
        node { 
            label 'linux'
            customWorkspace 'workspace/iast/'
        }
    }

    stages {
        stage('Build & Test') {
            steps {
                script {
                    def app = docker.build 'app'
                    app.withRun {c ->
                        sh '''
                            pip3 install -U pytest
                            pytest
                        '''
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}