pipeline {
	agent any
	tools {maven 'maven'}
	stages{
		stage('git-clone'){
			steps{
			     checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'git-check', url: 'https://github.com/Favouredd/module2_ci.git']]])	
			}
		}
		stage('etech-hello'){
			steps{
				sh 'git version'
			}
		}
       stage('Build Artifact - Maven') {
          steps {
            sh "mvn clean package -DskipTests=true"
            archive 'target/*.jar'
           }
       }
   }
}
