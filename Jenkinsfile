#!/usr/bin/env groovy

pipeline {
    agent any 
    stages {
        stage('Unit Test') {
            steps {
                git(url: "https://github.com/dsirine/pipeline", branch: "${ghprbSourceBranch}")
                sh "npm install"
                sh "npm test"
            }
        }
    }
}
