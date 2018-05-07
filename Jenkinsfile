/**
 * This pipeline will execute a simple Maven build
 */

podTemplate(cloud: 'kubeLabIvan', label: 'build', containers: [
  containerTemplate(name: 'goss', image: 'aelsabbahy/goss:latest', ttyEnabled: true, command: 'cat')
  ]) {

  node('build') {
    stage('Build Lab') {
      checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/melphos/jenkins-shared-functions.git']]])
      container('goss') {
          sh 'goss add addr jenkins-ui:8080'
          
      }
    }
  }
  deleteDir()
}
