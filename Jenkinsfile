properties([pipelineTriggers([githubPush()])])
node('linux') { 
	agent any
	stage('Unit Tests') {		git 'https://github.com/akht8823/java-project.git'
		Steps {
			sh 'ant -f test.xml -v'	
			junit 'reports/result/*.xml'
			
		}
	}	stage('Build') { 
		Steps {
			sh 'ant'
			sh 'ant -f build.xml -v'
		}	}	}