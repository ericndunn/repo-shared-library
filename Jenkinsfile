// @Library('my-shared-libs@master')_
// evenOrOdd(currentBuild.getNumber())
@Library('my-shared-libs@feature/Test_Functions')_
pipeline {
    agent {
        label 'master'
  }
    stages {
        stage('test') {
            steps {
                node('windows') {
                sayHello 'Joe'
                }
            }
        }
        stage('Environment variables') {
            steps {
                node('windows') {
                bat('set')
                }
            }
        }
        stage('Version of PS') {
            steps {
                node('windows') {
                powershell label: '', script: '$PSVersionTable'
                }
            }
        }
        stage ('Example') {
            steps {
                script { 
                    buildPlugin name: 'script-security'
                }
            }
        }
        stage('Get-ChildItem') {
            steps {
                node('windows') {
                powershell label: '', script: '''Get-ChildItem |
                Sort-Object -Property LastWriteTime, Name |
                Format-Table -Property LastWriteTime, Name'''
                }
            }
        }
        stage('Get-CimInstance') {
            steps {
                node('windows') {
                powershell label: '', script: '''Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixID'''
                }
            }
        }
    }
}

