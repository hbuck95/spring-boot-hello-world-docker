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
		stage('---run---'){
			steps{
				sh "ssh -f jenkins@13.79.18.169 'java -jar /home/jenkins/deployments/hello-world-0.0.1-SNAPSHOT.jar &'"
			}
		}
        }
}
