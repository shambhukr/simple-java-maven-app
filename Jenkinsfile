pipeline {
		agent {
		label "docker"
		}
		stages {
			stage('Build') {
				steps {
					sh 'mvn -B -DskipTests clean package'
										
				}
			}		
			stage('Test') {
				steps {
					sh 'mvn test'
				}
				post {
					always {
						archive "target/**/*"
						junit 'target/surefire-reports/*.xml'
					}
				}
			}
			stage('Deliver') { 
				steps {
					sh './jenkins/scripts/deliver.sh' 
				}
			}							
		}			
}	
