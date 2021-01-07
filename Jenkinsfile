pipeline {

    agent {
        node {
            label 'master'
        }
    }

    options {
        buildDiscarder logRotator( 
                    daysToKeepStr: '16', 
                    numToKeepStr: '10'
            )
    }

    stages {
        
        stage('Cleanup Workspace') {
            steps {
                cleanWs()
                sh """
                echo "Cleaned Up Workspace For Project"
                """
            }
        }

        stage('Code Checkout') {
            steps {
                checkout([
                    $class: 'GitSCM', 
                    branches: [[name: '*/main']], 
                    userRemoteConfigs: [[url: 'https://github.com/spring-projects/spring-petclinic.git']]
                ])
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

    }   
    
            stage('Performance Test Deployed Code') {
            when {
                branch 'develop'
            }
            steps {
                sh """
                echo "pre-LTIP"
                """

                sh """
                echo "LTIP 1"
                """
            }
           steps {
                sh """
                echo "LTIP 2"
                """

                sh """
                echo "LTIP 3"
                """
            }
          steps {
                sh """
                echo "LTIP 4"
                """

                sh """
                echo "post-LTIP"
                """
            }
        }

    }
}
