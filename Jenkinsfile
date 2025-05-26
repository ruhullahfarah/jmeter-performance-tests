pipeline {
  agent any

  stages {
    stage('Run JMeter') {
      steps {
        sh 'jmeter -n -t simple-api-test.jmx -l results.jtl -e -o reports'
      }
    }
  }

  post {
    always {
      publishHTML([
        allowMissing: false,
        alwaysLinkToLastBuild: true,
        keepAll: true,
        reportDir: 'reports',
        reportFiles: 'index.html',
        reportName: 'JMeter Test Report'
      ])
    }
  }
}
