pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }
    stage('Run JMeter') {
      steps {
        // Use bat on Windows instead of sh
        bat 'jmeter -n -t testplan.jmx -l result.jtl -e -o reports'
      }
    }
    stage('Publish Report') {
      steps {
        publishHTML([allowMissing: false,
                     alwaysLinkToLastBuild: true,
                     keepAll: true,
                     reportDir: 'reports',
                     reportFiles: 'index.html',
                     reportName: 'JMeter Test Report'])
      }
    }
  }
}
