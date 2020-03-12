pipeline {
	agent any
	//triggers {
       // 	cron('0 9 1-7 * 1')
          //}  
	
	stages {
        //stage ("Other pipeline") {		//an arbitrary stage name
        //    steps {
        //        build 'listPlugins'	//this is where we specify which job to invoke.
        //    }
        //}
		
 stage('do something') {
        steps
	 {
	  script{
           def success = "SUCCESS"
def build_run
build_run = build job: 'listPlugins', propagate: false
println build_run.result
if (build_run.result == success)
    println('job1 passed')
else
    println('job1 failed')  
	  }
           
         }
    }
		stage('Build') {
			when{
				expression { branch 'master' || 'develop' }
			}
			
			agent any
			steps {
				sh "sleep 30" 
				echo 'HELLO WORLD'
				sh 'printenv'
				echo GIT_BRANCH
				
				script{
				def GIT_COMMITTER_EMAIL = sh (
      					script: 'git --no-pager show -s --format=\'%ae\'',
      					returnStdout: true
				).trim()
				echo GIT_COMMITTER_EMAIL
				}
			}
		}
		stage('Test') {
			steps {
				unstash 'myApp'
				echo 'testing...'
			}
		}
		stage('Approval') {
			// no agent is used, so executors are not used up when waiting for approvals
			agent none
			steps {
				checkpoint 'ready for approval'
				script {
					def approver = input id: 'Deploy', message: 'Deploy to production?', submitter: 'rkivisto,admin', submitterParameter: 'deploy_approver'
					echo "This deployment was approved by ${approver}"
				}
				// This milestone will abort all older builds than this one
				// so old builds don't get deployed to production
			milestone label: 'deploy', ordinal: 2
			}
		}
		//stage('Deploy') {
		//	agent any
		///	steps {
		//		lock(resource: 'deployApplication'){
		//			unstash 'myApp'
		//			echo 'Deploying...'
		//		}
		//	}
		//}
	}
}
