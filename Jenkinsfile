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
		stage('---SSH to Live---'){
			steps{
				sh "ssh jenkins@13.79.18.169"
			}
		}
		stage('---deploy---'){
			steps{
				sh "cd ~/deployments/"
				sh "scp jenkins@13.79.18.163:/var/lib/jenkins/workspace/HelloWorld-Pipe/target/hello-world-0.0.1-SNAPSHOT.jar ."
			}
		}
		stage('---run---'){
			steps{
				sh "java -jar ./hello-world-0.0.1-SNAPSHOT.jar"
			}
		}
        }
}
