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
        withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: '8e1a0b06-5f11-4485-97fb-44e335762aba', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) 
        {
        sh 'aws cloudformation describe-stack-resources --stack-name jenkins --region us-east-1' 
        }
	}
}
  