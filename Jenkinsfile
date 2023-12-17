pipeline {
    agent any
        stages {
            stage('Download Repo') {
                steps {
                    // Get some code from a GitHub repository
                    git 'https://github.com/ksnithya/helm-nithya.git'
                }
            }
            stage('check chart exist'){
                steps{
                    script{
                        def x = sh(script: "helm status nithya | wc -l", returnStdout: true)
                        if (x.toInteger() > 0){
                            sh '''cd nithya
                            helm uninstall nithya
                            helm install nithya .
                            '''
                        } else {
                            sh '''cd nithya
                            helm install nithya .
                            '''                            
                        }
                    }
                }
            }
        }
}
