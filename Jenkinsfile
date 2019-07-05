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
				sh "ssh jenkins@13.79.18.169"
				sh "scp jenkins@13.79.18.163:~/var/lib/jenkins/workspace/spring-boot-hello-world-docker/target/hello-world-0.0.1-SNAPSHOT.jar ~/deployments"
			}
		}
		stage('---run---'){
			steps{
				sh "java -jar ~/deployments/hello-world-0.0.1-SNAPSHOT.jar"
			}
		}
        }
}
