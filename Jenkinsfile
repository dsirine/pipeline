#!/usr/bin/env groovy

pipeline {
    agent any 
    stages {
        stage('Unit Test') {
            steps {
                git "https://github.com/dsirine/pipeline"
                sh "npm install"
                sh "npm test"
            }
        }
    }
}
