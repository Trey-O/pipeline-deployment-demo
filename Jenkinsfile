pipeline {
	agent none
	stages {
		stage('Build') {
			agent any
			steps {
				// https://jenkins.io/blog/2016/10/16/stage-lock-milestone/
				// The first milestone step starts tracking concurrent build order
				milestone label: 'build', ordinal: 1
				echo 'compiling...'
				sh 'touch a.jar'
				sh 'printenv' 
				stash includes: 'a.jar', name: 'myApp'
				echo '${git.branchName}'
				echo '${git.BRANCHNAME}'
				echo '$BRANCH_NAME'
				echo '${git.GIT_LOCAL_BRANCH}'
				echo '${GIT_LOCAL_BRANCH}'
				echo '$GIT_LOCAL_BRANCH'
				echo 'GIT_BRANCH'
				echo 'GIT_LOCAL_BRANCH'
				echo 'env.GIT_LOCAL_BRANCH'
				echo '${env.GIT_LOCAL_BRANCH}'
			}
		}
	}
}
