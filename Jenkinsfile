/**
 * This pipeline will execute a simple Maven build
 */

podTemplate(cloud: 'kubeLabIvan', label: 'build', containers: [
  containerTemplate(name: 'goss', image: 'busybox', ttyEnabled: true, command: 'cat')
  ]) {

  node('build') {
    stage('Build Lab') {
      checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/melphos/jenkins-shared-functions.git']]])
      container('goss') {
          sh 'ls -l'
          sh 'pwd'
          sh 'du -h --max-depth=1 .'
      }
    }
  }
  deleteDir()
}
