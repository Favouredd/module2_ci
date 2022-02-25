pipeline{
   agent any
   tools {maven 'maven'}
   stages{
    stage('git-clone'){
            steps{
              checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'GitHUB-CREDENTIALS', url: 'https://github.com/Favouredd/module2_ci.git']]])
          }    
      }
    
