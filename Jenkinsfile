@Library('my-shared-library')_
sayHello 'Trey'

node{
checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], gitTool: 'Default', submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/Trey-O/pipeline-deployment-demo']]])
}




