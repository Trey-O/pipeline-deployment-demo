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
				//sh 'GIT_LOCAL_BRANCH'
				sh 'echo $GIT_LOCAL_BRANCH'
				//sh '''
    				//    git rev-parse --abbrev-ref HEAD > 'GIT_BRANCH'
    				//    git_branch = readFile('GIT_BRANCH').trim()
    				//    echo git_branch
   				 //  '''
				step{
				def git_branch
    				git_branch = sh returnStdout: true, script: "git rev-parse --abbrev-ref HEAD"
				//sh "git_branch= cat GIT_BRANCH"
				sh "echo ${git_branch}"
				}
				
			}
		}
	}
}
