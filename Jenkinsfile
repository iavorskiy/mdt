pipeline {
    agent {
        label 'nod3'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
         stage('uptime') {
            steps {
                sh 'ssh ec2-user@34.251.208.9 uptime'
            }
        }
        stage('stage 1') {
            steps {
                echo 'Stage1'
            }
        }
        stage('Parallel') {
            parallel {
                stage('Stage2-parallel') {
                    when { branch 'master' }
                    steps {
                        echo 'Stage2'
                    }
                }
                stage('Stage3 - parallel') {
                    when { not { branch 'master' } }
                    steps {
                        echo 'Stage3'
                    }
                }
            }
        }
        stage('Optional') {
            when {
                expression {params.DOIT == true}
            }
            steps {
                echo 'Do It'
            }
        }
    }
}
