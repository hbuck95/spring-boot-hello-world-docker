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
		stage('---pwd---'){
			steps{
				sh "pwd"
			}
		}
		stage('--test copy---'){
			steps{
				sh "scp ~/myfile2  jenkins@13.79.18.169:~/"
			}
		}
		stage('---deploy---'){
			steps{
				sh "scp /var/lib/jenkins/workspace/HelloWorld-Pipe/target/hello-world-0.0.1-SNAPSHOT.jar jenkins@13.79.18.169:~/deployments/"
			}
		}
		stage('---run---'){
			steps{
				sh "ssh jenkins@13.79.18.169"
				sh "java -jar /home/jenkins/deployments/hello-world-0.0.1-SNAPSHOT.jar"
			}
		}
        }
}
