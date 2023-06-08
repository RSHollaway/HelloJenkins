#!/usr/bin/env groovy

pipeline {
    agent any
    options {
        skipDefaultCheckout(false)
    }
    stages {
        stage('Clean WorkSpace') {
            steps {
                cleanWs()
                checkout scm 
            }
        }
        stage('Show Env Vars') {
            steps {
                echo "Building ${env.JOB_NAME}..."
                echo "Build ID ${env.BUILD_ID}..."
                echo "Build Number ${env.BUILD_NUMBER}..."
                echo "Jenkins URL ${env.JENKINS_URL}..."
                echo "Workspace ${env.WORKSPACE}..."
                pwsh 'write-host "Hello PowerShell"'
               
            }
        }
        stage('Perform Commands') {
            steps {
                pwsh 'write-host "Hello PowerShell"' 
            }
        }
        stage('Ping Local Host') {
            steps {
                sh 'ping -c 5 127.0.0.1'
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
