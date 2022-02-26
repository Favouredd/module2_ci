pipeline {
	agent any
	tools {maven 'Maven'}
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
       stage('Unit Tests - JUnit and JaCoCo') {
          steps {
             sh 'mvn test'
             }
             post {
               always {
                 junit 'target/surefire-reports/*.xml'
                 jacoco execPattern: 'target/jacoco.exec'
        }
      }
    }       
      stage('Mutation Tests - PIT') {
         steps {
           sh "mvn org.pitest:pitest-maven:mutationCoverage"
      }
          post {
            always {
          pitmutation mutationStatsFile: '**/target/pit-reports/**/mutations.xml'
        }
      }
    }
  }
}
