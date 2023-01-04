pipeline {
    agent any
    options {
        buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')
    }
    stages {
        parallel{
            stage('Say Hello') {
                steps {
                    sh '''
                    echo Hello!
                    '''
                }
            }
            stage('Wish Everyone') {
                steps {
                    sh '''
                    echo hello world!
                    '''
                }
            }
        }
    }
}