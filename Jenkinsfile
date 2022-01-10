pipeline{
    agent any
    
    stages {
        
        stage('Build Docker Image') {
            steps {
                script {
                  sh 'docker build -t myapp .'
                }
            }
        }
        stage('Deploy Docker Image') {
            steps {
                script {
                 withCredentials([string(credentialsId: 'dockerhub-pwd', variable: 'dockerhubpwd')]) {
                    sh 'docker login -u devopshint -p ${dockerhubpwd}'
                 }  
                 sh 'docker push devopshint/myapp'
                }
            }
        }
    }
}