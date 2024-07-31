#!/usr/bin/env groovy

pipeline {
  agent any

  tools{
     maven 'maven'
  }
  stages {
    stage('build jar'){
      steps {
          script{
            echo "Building jar fle"
            sh "mvn package"
          }
      }
    }
    stage('build docker image'){
      steps {
          script{
            echo "Building a docker file"
            sh "docker build -t my-pipeline-build:1.0 ."
          }
      }
    }
  }
}
