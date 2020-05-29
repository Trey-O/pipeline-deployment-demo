pipeline{
	agent any
	@Library('my-shared-library')_

	stages{
		stage('Demo'){
			echo "DO THE CHECKOUT:"
			checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], gitTool: 'Default', submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/Trey-O/pipeline-deployment-demo']]])
    			echo "POST CHECKOUT:"
			echo 'Hello world'
    			sayHello 'Dave'	
		}
	}
}
