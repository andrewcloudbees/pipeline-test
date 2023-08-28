pipeline {

//    agent any
    agent any //{ node { label 'remote' } }

    stages {
        
        stage('Cleanup Workspace') {
            steps {
                sh """
                echo "Cleaned Up Workspace For Project"
                """
            }
        }

        stage('Code Checkout') {
            steps {
                sh "echo 'Code Checked Out'"
                /*
                checkout([
                    $class: 'GitSCM', 
                    branches: [[name: '*//*main']], 
                    userRemoteConfigs: [[url: 'https://github.com/jhanger-cb/pl_git_test.git']]
                ])*/
                 
            }
        }

        stage('SonarQube Analysis') {
            steps {
                script {
                    def scannerHome = tool 'SonarScanner';
                    withSonarQubeEnv() {
                        sh "${scannerHome}/bin/sonar-scanner"
                    }
                }
            }
        }

        stage(' Unit Testing') {
            steps {
                sh """
                echo "Running Unit Tests"
                """
            }
        }

        stage('Code Analysis') {
            steps {
                sh """
                echo "Running Code Analysis"
                """
            }
        }

        stage('Build Deploy Code') {
            when {
                branch 'develop'
            }
            steps {
                sh """
                echo "Building Artifact"
                """

                sh """
                echo "Deploying Code"
                """
            }
        }
        
        stage('Publish') {
            steps {
                sh "echo 'testing tags'"
            }
        }

    }   
}
