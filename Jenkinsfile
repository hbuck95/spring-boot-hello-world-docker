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
				sh "scp /var/lib/jenkins/workspace/HelloWorld-Pipe/target/hello-world-0.0.1-SNAPSHOT.jar jenkins@13.79.18.169:~/deployments/"
			}
		}
		stage('---SSH---'){
			steps{
				sh "ssh jenkins@13.79.18.169"
			}
		}
		stage('---run---'){
			steps{
				sh "chmod 777 ~/deployments/hello-world-0.0.1-SNAPSHOT.jar"
				sh "java -jar ~/deployments/hello-world-0.0.1-SNAPSHOT.jar"
			}
		}
        }
}
