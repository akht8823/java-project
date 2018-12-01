properties([pipelineTriggers([githubPush()])])

node('linux') { 
	stage('Unit Tests') {
		git 'https://github.com/akht8823/java-project.git'
		sh 'ant -f test.xml -v'	
		junit "reports/result.xml" 	
		}
	stage ('Build') { 
		sh 'ant -f build.xml -v' 
		}
    stage ('Deploy') {
 		sh 'aws s3 cp /workspace/java-pipeline/dist/rectangle-*.jar s3://akht8823-assignment-10/'
       	}
    stage('Report'){	
        sh 'aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins' 
	}
}
   