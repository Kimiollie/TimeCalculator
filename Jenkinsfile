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
                                jacoco path: '**/target/jacoco.exec'
                            }
                        }
            }

            post {
                always {
                    junit '**/target/surefire-reports/*.xml'
                    jacoco path: '**/target/jacoco.exec'
                }
            }
        }