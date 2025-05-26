pipeline {
    agent any

    tools {
        jdk 'JDK17'         // Make sure this matches your Jenkins JDK install name
    }

    environment {
        JMETER_HOME = "/opt/apache-jmeter-5.5"  // Adjust to your JMeter install path
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/ruhullahfarah/jmeter-performance-tests.git'
            }
        }

        stage('Run JMeter Test') {
            steps {
                sh """
                    ${env.JMETER_HOME}/bin/jmeter -n -t simple-api-test.jmx -l results.jtl -e -o report
                """
            }
        }

        stage('Publish Report') {
            steps {
                publishHTML([
                    reportDir: 'report',
                    reportFiles: 'index.html',
                    reportName: 'JMeter HTML Report'
                ])
            }
        }
    }
}
