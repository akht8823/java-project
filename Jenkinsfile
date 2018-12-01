properties([pipelineTriggers([githubPush()])])
node('linux') { 
	stage('Unit Tests') {		git 'https://github.com/akht8823/java-project.git'
		sh 'ant'
		junit 'reports/result.xml'
		sh 'ant -f test.xml -v'		
	}	stage('Build') { 
		sh 'ant'
		sh 'ant -f build.xml -v'	}	stage('Report') {		junit 'reports/*.xml' 
	}}