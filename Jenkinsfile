@Library('my-shared-library')_
pipeline{
	agent any
	

	stages{
		
		stage('Demo'){
			steps {
				echo "DO THE CHECKOUT:"
				checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], gitTool: 'Default', submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/Trey-O/pipeline-deployment-demo']]])
    				echo "POST CHECKOUT:"
				echo 'Hello world'
    				sayHello 'Dave'	
			}
		}
	}
}
