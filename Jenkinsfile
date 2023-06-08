#!/usr/bin/env groovy

pipeline {
    agent any
    options {
        skipDefaultCheckout(true)
    }
    stages {
        stage('Build') {
            steps {
                cleanWs()
                checkout scm
                echo 'Building ${env.JOB_NAME}...' 
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