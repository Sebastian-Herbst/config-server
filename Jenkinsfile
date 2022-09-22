pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                git(branch: 'main', url: 'https://github.com/Sebastian-Herbst/config-server.git')
            }
        }

        stage('List directory') {
            parallel {
                stage('List directory') {
                    steps {
                        sh 'ls -la'
                    }
                }

                stage('Unit & Integration Tests') {
                    steps {
                        script {
                            try {
                                sh './gradlew clean test --no-daemon' //run a gradle task
                            } finally {
                                junit '**/build/test-results/test/*.xml'
                                //make the junit test results available in any case (success & failure)
                            }
                        }
                    }
                }
            }
        }
    }
}