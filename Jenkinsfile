pipeline {
    agent any
    tools {
        jdk 'AdoptJDK17'
    }
    stages {
        stage('Checkout Code') {
            steps {
                git(branch: 'main', url: 'https://github.com/Sebastian-Herbst/config-service.git')
            }
        }

        stage('Test') {
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
        stage('Build') {
            steps {
                script {
                    sh './gradlew build --no-daemon' //run a gradle task
                }

            }
        }
        stage('Deploy') {
            steps {
                script {
                    sh './gradlew jib --no-daemon' //run a gradle task
                }

            }
        }
    }
}