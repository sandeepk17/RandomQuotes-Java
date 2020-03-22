pipeline {
    agent {
        // Set Build Agent as Docker file 
        dockerfile true
    }
    environment {
        // Set env variables for Pipeline
        IMAGE = readMavenPom().getArtifactId()
        VERSION = readMavenPom().getVersion()
        ARTIFACTORY_SERVER_ID = "Artifactory1"
        ARTIFACTORY_URL = "http://192.168.0.104:8081/artifactory"
        ARTIFACTORY_CREDENTIALS = "admin.jfrog"
        CURRENT_BUILD_NO = "${currentBuild.number}"
        RELEASE_TAG = "${currentBuild.number}-${VERSION}"
        CURRENT_BRANCH = "${env.BRANCH_NAME}"
        OCTOHOME = "${OCTO_HOME}"
    }

    options {
        // Set Jenkins Pipeline options
        buildDiscarder(logRotator(numToKeepStr: '30', artifactNumToKeepStr: '30'))
        timestamps()
        disableConcurrentBuilds()
    }

    stages {
        stage ('Environmental Variables') {
            steps {
                echo "Test stage"
            }
        }
        stage('Build') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    mvn --version 
                '''
                echo "${VERSION}"
                echo "${IMAGE}"
                echo "${CURRENT_BRANCH}"
                echo "$WORKSPACE"
                sh 'mvn clean test package deploy -s settings.xml'
            }
        }
        stage('Test') {
            steps {
                echo "Test stage"
            }
        }
        
        stage('Octopus Deploy') {
            steps{        
                echo "Test stage"
            }
        }

        stage('Smoke test') {
            steps{        
                echo "Smoke Test stage"
            }
        }

        stage('Integration Test') {
            steps{        
                echo " Deploy to artifactory"
            }
        }

        stage('Deploy') {
            steps{        
                echo " Deploy to artifactory"
            }
        }
    }
}