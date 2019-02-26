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
        sh 'sonar-scanner   -Dsonar.projectKey=test   -Dsonar.sources=.   -Dsonar.host.url=http://www.dexemple.fr/sonarqube   -Dsonar.login=0da7debe9ac86ac45fbda7a957d3fb26127b507'
      }
    }
  }
}