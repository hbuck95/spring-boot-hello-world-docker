pipeline{
        agent any
        stages{
                stage('---clean---'){
                        steps{
                                sh "mvn clean"
                        }
                }
                stage('---package---'){
			steps{
				sh "mvn package"
			}
		}
		stage('---deploy---'){
			steps{
				sh "scp -r /var/lib/jenkins/workspace/spring-boot-hello-world-docker/target/hello-world-0.0.1-SNAPSHOT.jar jenkins@13.79.18.169:~/deployments/
			}
		}
		stage('---run---'){
				sh "ssh jenkins@13.79.18.169"
				Sh "java -jar ~/deployments/hello-world-0.0.1-SNAPSHOT.jar
			}
		}
        }
}
