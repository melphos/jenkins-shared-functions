/**
 * This pipeline will execute a simple Maven build
 */

podTemplate(cloud: 'kubeLabIvan', label: 'build', containers: [
  containerTemplate(name: 'goss', image: 'aelsabbahy/goss:latest', ttyEnabled: true, command: 'cat'),
  containerTemplate(name: 'golang', image: 'golang:1.8.0', ttyEnabled: true, command: 'cat')
  ]) {

  node('build') {
    stage('Build Lab') {
      checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/melphos/jenkins-shared-functions.git']]])
      container('goss') {
          sh 'goss add addr jenkins-ui:8080'
          sh 'goss validate'
          
      }
    }
    stage('Get a Golang project') {
            git url: 'https://github.com/hashicorp/terraform.git'
            container('golang') {
                stage('Build a Go project') {
                    sh """
                    mkdir -p /go/src/github.com/hashicorp
                    ln -s `pwd` /go/src/github.com/hashicorp/terraform
                    cd /go/src/github.com/hashicorp/terraform && make core-dev
                    """
                }
            }
        }
  }
  
}
