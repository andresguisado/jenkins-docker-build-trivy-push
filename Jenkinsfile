#!/usr/bin/env groovy
pipeline {
    agent any
    stages {
        stage ('Build Image') {
            steps {
                sh "docker build -t andresguisado/alpine-trivy:latest ."
            }
        }
        stage ('Scanning Image') {
            steps {
                sh "trivy --exit-code 1 --severity HIGH --no-progress andresguisado/alpine-trivy:latest"
            }
        }
        stage ('Push Image') {
            steps {
                sh "docker push andresguisado/alpine-trivy:latest"
            }
        }
    }
}