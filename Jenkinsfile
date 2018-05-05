/**
 * This pipeline will execute a simple Maven build
 */

podTemplate(label: 'maven', containers: [
  containerTemplate(name: 'maven', image: 'maven:3.5-jdk-8-alpine', ttyEnabled: true, command: 'cat')
  ]) {

  node('maven') {
    stage('Build CadastroPortal Backend') {
      git branch: 'development', credentialsId: '07b56e83-265b-42b4-9fd2-25c6fd72f101', url: 'http://gitlab.mctic.gov.br/COMPONENTES-CORPORATIVOS/CADASTROPORTAL/cadastroportal-backend.git'
      /* COMPONENTES-CORPORATIVOS/CADASTROPORTAL/cadastroportal-backend.git */
      container('maven') {
          sh 'mvn -B -X clean pakage'
      }
    }
  }
}
