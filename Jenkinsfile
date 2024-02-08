pipeline {
	agent {
		label "ubuntu-lable"
	}
	stages {
		stage ("Pulling the code from SCM") {
			steps {
				git branch: 'main', url: 'https://github.com/gouravaas/new_java_app.git'
			}
		}
		stage ("Build the code") {
			steps {
				sh 'sudo mvn dependency:purge-local-repository'
                                sh 'sudo mvn clean package'
			}
		}
		stage ("Testing the Build dd"){
			steps {
				sh 'sudo docker build -t java-app:$BUILD_TAG .'
				sh 'sudo docker run -dit --name java_app -p 8080:8080 java-app:$BUILD_TAG'
			}
		}
	}

}
