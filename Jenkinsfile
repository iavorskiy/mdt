pipeline {
    agent {
        label 'demo'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/dbielik/mdt'
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
                    steps {
                        echo 'Stage2'
                    }
                }
                stage('Stage3 - parallel') {
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
