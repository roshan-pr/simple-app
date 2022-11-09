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
                            apt-get update
                            apt-get install -y python3
                            python3 --version
                        '''
                    }
                }
                stage('Stage-2') {
                    agent {
                        docker { image 'ubuntu' }
                    }
                    steps {
                        sh '''
                            echo Running parallel
                            for i in {1..20} ; do sleep 1; echo -ne '.' ; done
                        '''
                    }
                }
            }
        }
    }
}