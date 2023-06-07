pipeline
{
	agent any	
	stages
	{
		stage("Sourcecode-Checkin")
		{
			steps
			{
			git branch: 'main', url: 'https://github.com/nocturnaldevops/Project1.git'
			mail bcc: '', body: 'The source code from the project https://github.com/nocturnaldevops/Project1.git is successfully cloned', cc: '', from: '', replyTo: '', subject: 'source code successfully cloned', to: 'nocturnaldevops@gmail.com'
			}
		}
		stage("Build")
		{
			steps
			{
			sh 'mvn packge'
			mail bcc: '', body: 'build success', cc: '', from: '', replyTo: '', subject: 'build success', to: 'nocturnaldevops@gmail.com'
			}
		}
		stage("DeploytoTestEnv")
		{
			steps
			{
			mail bcc: '', body: '''Dear Ms. Jaya
The project Pr1010101  is waiting for your approval
Please take necessary action 
Thanks 
Prashanth''', cc: '', from: '', replyTo: '', subject: 'Waiting for approval for the project: Prid10101', to: 'nocturnaldevops@gmail.com'
			input message: 'waiting for approval from Jaya', submitter: 'jaya'
			deploy adapters: [tomcat9(credentialsId: 'd50fcc35-da87-45f7-a21f-4f03fa75ee9f', path: '', url: 'http://172.31.2.65:8080')], contextPath: 'devopstest1', war: '**/*.war'
			}
		}
		}
		post
		{
		success
		{
		mail bcc: '', body: 'Project Success', cc: '', from: '', replyTo: '', subject: 'the proect is successfully  done', to: 'nocturnaldevops@gmail.com'
		}
		failure
		{
		mail bcc: '', body: 'Project Failed!!', cc: '', from: '', replyTo: '', subject: 'Project Failed!!!', to: 'nocturnaldevops@gmail.com'
		}
		}
		}
