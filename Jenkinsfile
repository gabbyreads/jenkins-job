#!/usr/bin/env groovy
dev gv
pipeline {
  agent any

  tools{
     maven 'maven'
  }
  stages {
    stage('init'){
      steps {
          script{
            gv = load "script.groovy"
          }
      }
    }
    stage('build jar'){
      steps {
          script{
            gv.getName()
            echo "Building jar fle"
            sh "mvn package"
          }
      }
    }
    stage('build docker image'){
      steps {
          script{
            echo "Building a docker file"

            withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'PASS', usernameVariable: 'USER')]){
               sh 'docker build -t gabrielomokpo/my-pipeline:jma-1.0 .'
               sh "echo $PASS | docker login -u $USER --password-stdin"
               sh 'docker push gabrielomokpo/my-pipeline:jma-1.0'
            }
          }
      }
    }
    stage('deploying'){
       steps{
         script{
           echo 'deploying..'
         }
       }
    }
  }
}
