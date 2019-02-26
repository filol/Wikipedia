pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh '''npm i
npm run build
cp -rf dist/ /var/www/html/Wikipedia/'''
      }
    }
    stage('Run Sonar') {
      steps {
        sh '''sonar-scanner \\
  -Dsonar.projectKey=Wikipedia \\
  -Dsonar.sources=src/ \\
  -Dsonar.host.url=http://www.dexemple.fr/sonarqube \\
  -Dsonar.login=0771a5272b02b6501fb8edc28842e103ba0a8876'''
      }
    }
  }
}