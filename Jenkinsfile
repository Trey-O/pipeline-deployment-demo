pipeline {
	agent none
	triggers {
        	cron('')
    	}
	stages {
		stage('Build') {
			agent any
			steps {
				sh 'printenv'
				echo GIT_BRANCH
				// https://jenkins.io/blog/2016/10/16/stage-lock-milestone/
				// The first milestone step starts tracking concurrent build order
				//milestone label: 'build', ordinal: 1
				//echo 'compiling...'
				//sh 'touch a.jar'
				//stash includes: 'a.jar', name: 'myApp'
			}
		}
		stage('Release Branch Test') {
                    when {
                        branch 'release'
                    }
                    steps {
			    echo 'Release Branch'
                //withCredentials([usernamePassword(credentialsId: '4b33463f-c57a-4b3e-a54b-97faeb0c22cb', passwordVariable: 'docker_password', usernameVariable: 'docker_username')]) {
                   // sh 'mkdir .docker || echo ".docker directory exists"'
                    //sh 'export DOCKER_CONFIG=`pwd`/.docker'
                    //sh 'docker login --username=$docker_username --password=$docker_password $artUrl'
                    //sh 'docker build --no-cache -t dps-ingest-api:$BRANCH_TAG-$VERSION .'

                    //sh 'docker tag dps-ingest-api:$BRANCH_TAG-$VERSION $artUrl/preservation/dps-ingest-api:$BRANCH_TAG-$VERSION'
                    //sh 'docker push $artUrl/preservation/dps-ingest-api:$BRANCH_TAG-$VERSION'

                }
                    }
	stage('2nd Stage ch-lane') {
                    when {
                        branch 'consolidation'
                    }
                    //environment {
                    //    DOCKER_HOST = "tcp://L17067:2375"
                    //}
                    steps {
			    echo 'Consolidation Branch' 
                      //  sh 'docker rm -f dps-ingest-api || :'
                      //  sh 'docker image prune -a -f'
                      //  sh 'docker pull $artUrl/preservation/dps-ingest-api:$BRANCH_TAG-$VERSION'
                       // sh 'BUILD_ID=$BRANCH_TAG-$VERSION && /usr/local/bin/docker-compose -f docker-compose.build.yml up -d'
                       // sh '/usr/bin/bash -x health_mon/build/health_check.sh'
                    }
        }

		//stage('Test') {
		//	agent any
		//	steps {
		//		unstash 'myApp'
		//		echo 'testing...'
		//	}
		//}
		//stage('Approval') {
		//	// no agent is used, so executors are not used up when waiting for approvals
		//	agent none
		///	steps {
		//		checkpoint 'ready for approval'
		//		script {
		//			def approver = input id: 'Deploy', message: 'Deploy to production?', submitter: 'rkivisto,admin', submitterParameter: 'deploy_approver'
		//			echo "This deployment was approved by ${approver}"
		//		}
				// This milestone will abort all older builds than this one
				// so old builds don't get deployed to production
		//		milestone label: 'deploy', ordinal: 2
		//	}
		//}
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
