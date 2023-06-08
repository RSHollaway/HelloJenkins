#!/usr/bin/env groovy

pipeline {
    agent any
    options {
        skipDefaultCheckout(false)
    }
    stages {
        stage('Build') {
            steps {
                cleanWs()
                checkout scm
                echo "Building ${env.JOB_NAME}..."
                echo "Build ID ${env.BUILD_ID}..."
                echo "Build Number ${env.BUILD_NUMBER}..."
                echo "Jenkins URL ${env.JENKINS_URL}..."
                echo "Workspace ${env.WORKSPACE}..."
                //sh 'ping -c 5 192.168.178.128'
               
            }
        }
    }
    post {
        always {
            cleanWs(cleanWhenNotBuilt: false,
                    deleteDirs: true,
                    disableDeferredWipeout: true,
                    notFailBuild: true,
                    patterns: [[pattern: '.gitignore', type: 'INCLUDE'],
                               [pattern: '.propsfile', type: 'EXCLUDE']])
        }
        }
    }
