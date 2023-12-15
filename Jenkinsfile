pipeline {
   agent any
 
   environment {
       GIT_REPO_URL = 'https://github.com/snehithkolli/jenkins.git'
       NGINX_PATH = "\\Users\\snehithreddykolli\\Downloads\\nginx-1.24.0\\html.docs"
   }
 
   stages {
       stage('Checkout') {
           steps {
               script {
                   // Use the checkout step to clone the Git repository
                  checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: '40e70ee1-e6b2-4da7-b199-3de28af6dd65', url: 'https://github.com/snehithkolli/jenkins.git']])
               }
           }
       }
 
       stage('Deploy to Nginx') {
           steps {
               script {
                   // Using the Jenkins workspace variable to reference files
                   bat 'xcopy /y "\\Users\\snehithreddykolli\\Downloads\\jenkinsline\\index.html" "%NGINX_PATH%" '
               }
           }
       }
   }
 
   post {
       success {
           echo 'Pipeline succeeded! You can add additional steps here.'
       }
       failure {
           echo 'Pipeline failed! You may want to take some actions.'
       }
   }
}
