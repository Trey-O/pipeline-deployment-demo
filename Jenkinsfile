pipeline {
  agent {
    label 'ssh'
  }
  stages {
    stage('Build') {
      when {
        expression {
          return commitName.contains("admin")
        }

      }
      steps {
        sh 'git log -1 --format=\'%an <%ae>\''
        echo commitName
        sh 'git show --name-only'
        milestone(label: 'build', ordinal: 1)
        echo 'compiling...'
        sh 'touch a.jar'
        stash(includes: 'a.jar', name: 'myApp')
      }
    }
    stage('CustomTesting') {
      steps {
        echo 'Custom Testing beginning with script and for loops to run'
        script {
          ArrayList<String> arrayList = new ArrayList<String>();
          arrayList.add("A");
          arrayList.add("B");
          arrayList.add("C");
          for (int i = 0; i < arrayList.size(); i++) {
            stage("Internal For Loop Stage") {
              checkpoint "nested stage for loop checkpoint"
              echo "test"
            }
          }
        }

      }
    }
    stage('ViewTest') {
      steps {
        echo 'CAN YOU SEE IT????'
        echo 'testing'
      }
    }
    stage('Test') {
      when {
        expression {
          return commitName.contains("admin")
        }

      }
      steps {
        unstash 'myApp'
        echo 'testing...'
      }
    }
    stage('Approval') {
      when {
        expression {
          return commitName.contains("admin")
        }

      }
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
      when {
        expression {
          return commitName.contains("admin")
        }

      }
      steps {
        unstash 'myApp'
        echo 'Deploying...'
      }
    }
  }
  environment {
    commitName = sh(script: "git log -1 --format='%an <%ae>'", returnStdout: true)
  }
}