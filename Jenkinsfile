pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'git log --format=\'%an <%ae>\' GIT_COMMIT_ID'
        sh 'git show --name-only'
        milestone(label: 'build', ordinal: 1)
        echo 'compiling...'
        sh 'touch a.jar'
        stash(includes: 'a.jar', name: 'myApp')
      }
    }
    stage('Test') {
      steps {
        unstash 'myApp'
        echo 'testing...'
      }
    }
    stage('Approval') {
      steps {
        checkpoint 'ready for approval'
        script {
          def approver = input id: 'Deploy', message: 'Deploy to production?', submitter: 'rkivisto,admin', submitterParameter: 'deploy_approver'
          echo "This deployment was approved by ${approver}"
        }

        milestone(label: 'deploy', ordinal: 2)
      }
    }
    stage('Deploy') {
      steps {
        unstash 'myApp'
        echo 'Deploying...'
      }
    }
  }
}