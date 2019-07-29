#!/usr/bin/env groovy

stage("Unit Tests") {
  git(url: "https://github.com/dsirine/pipeline.git", branch: "${ghprbSourceBranch}")
  sh "npm install"
  sh "npm test"
}