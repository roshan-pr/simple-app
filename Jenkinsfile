pipeline {
    agent any
    options {
        buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')
    }
    stages {
        stage('Hello') {
            steps {
                sh '''
                echo hello world!
                '''
            }
        }
        stage('cat README') {
            when {
                branch "fix-*"
            }
            steps {
                sh '''
                cat README.md
                '''
            }
        }
        stage('Parallel-stages') {
            parallel {
                stage('Stage-1') {
                    agent {
                        docker { image 'debian'}
                    }
                    
                    steps {
                        sh '''
                            echo Running parallel stage 1
                            for i in {1..20} ; do sleep 1; echo -ne '.' ; done
                        '''
                    }
                }
                stage('Stage-2') {
                    agent {
                        docker { image 'ubuntu' }
                    }
                    steps {
                        sh '''
                            echo Running parallel stage 2
                            for i in {100..120} ; do sleep 1; echo -ne '.' ; done
                        '''
                    }
                }
            }
        }
    }
}