pipeline {
    agent any {
        stages {
            stage('One') {
                steps {
                    echo 'hi'
                }
            }
            stage('Two') {
                steps {
                    input('Do you want to proceed?')
                }
            }
            stage('Three') {
                when {
                    not {
                        branch "master"
                    }
                }
                steps{
                    echo "Hi"
                }
            
            }
            stage('Four') {
                parallel {
                    stage('Unit Test') {
                        steps {
                            echo 'Running Unit test.......'
                        }
                    }
                    stage('Integration test') {
                        agent {
                            docker {
                                reuseNode false
                                image 'ubuntu'
                            }
                        }
                        steps {
                            echo 'Running the Integration test .....'
                        }
                    }
                }
            }
        }
    }
}