#!/usr/bin/env groovy

pipeline {
    agent any
    options {
        skipDefaultCheckout(false)
    }
    stages {
        stage('Clean WorkSpace') {
            steps {
                cleanWs deleteDirs: true
                checkout scm 
            }
        }
        stage('Show Env Vars') {
            steps {
                sleep 2
                ansible.builtin.debug: msg="Starting Windows baseline playbook..."
                echo "Building ${env.JOB_NAME}..."
                sleep 2
                echo "Build ID ${env.BUILD_ID}..."
                sleep 2
                echo "Build Number ${env.BUILD_NUMBER}..."
                sleep 2
                echo "Jenkins URL ${env.JENKINS_URL}..."
                sleep 2
                echo "Workspace ${env.WORKSPACE}..."
            }
        }
        stage('Perform Commands') {
            steps {
                pwsh 'write-host "Hello PowerShell"' 
            }
        }
        stage('Ping Local Host - Bash') {
            steps {
                echo "Pinging Localhost with bash"
                sh 'ping -c 5 127.0.0.1'
            }}
        stage('Sleep') {
            steps {
                echo "Sleeping for 10 Seconds"
                sleep 10
            }}
        stage('Ping Local Host - PowerShell') {
            steps {
                echo "Pinging Localhost with PowerShell"
                pwsh 'test-connection -TargetName localhost'
            }
        }
        stage('Get Local Host - PowerShell') {
            steps {
                echo "Get Localhost with PowerShell"
                pwsh 'get-host'
            }
        }
        stage('Get Uptime - PowerShell') {
            steps {
                echo "Get Uptime with PowerShell"
                pwsh 'get-uptime | format-table'
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
