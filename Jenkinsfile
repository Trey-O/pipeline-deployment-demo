pipeline {
	agent none
	stages {
		stage('Build') {
			agent any
			steps {
				script{
					def branch_name
					branch_name = sh returnStdout: true, script: "git branch -a --contains ${GIT_LOCAL_BRANCH}"
					sh "echo ${branch_name}"
					sh 'git branch -a'
				}
			}
		}
	}
}
