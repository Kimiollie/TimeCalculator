pipeline {
            agent any

            tools {
                    maven 'Homebrew Maven'
                }

            stages {
                    stage('Checkout') {
                        steps {
                            git branch: 'main', url: 'https://github.com/Kimiollie/TimeCalculator.git'
                        }
                    }


                stage('Build') {
                    steps {
                        sh 'mvn clean install'
                    }
                }

                stage('Test') {
                    steps {
                        sh 'mvn test'
                    }
                }

                stage('Code Coverage') {
                    steps {
                        sh 'mvn jacoco:report'
                    }
                }
            }

            post {
                always {
                    junit '**/target/surefire-reports/*.xml'
                    publishCoverage adapters: [jacocoAdapter('**/target/site/jacoco/jacoco.xml')]
                }
            }
        }