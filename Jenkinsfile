pipeline {
    agent {
        kubernetes {
            cloud 'staging-k8s'
            yaml """
kind: Pod
metadata:
    name: jenkins-slave
spec:
    containers:
    - name: android
        image: thyrlian/android-sdk:latest
        imagePullPolicy: Always
"""
        }
    }

    stages {
        stage("checkout") {
            steps { 
                container('android') {
                    checkout scm
                }
            } 
        }
        stage("test") { steps { container('android') { echo 'ls' } } }
        stage("build") { steps { container('android') { echo 'echo build' } } }
    }
}
