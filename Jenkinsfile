#!/usr/bin/env groovy

pipeline {
  agent any

  tools{
     maven 'maven'
  }
  stages {
    stage('build'){
      steps {
          script{
            echo "Building jar fle"
            sh "mvn package"
          }
      }
    }
  }
}
