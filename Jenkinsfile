#!/usr/bin/env groovy

/* Only keep the 10 most recent builds. */
def projectProperties = [
    [$class: 'BuildDiscarderProperty',strategy: [$class: 'LogRotator', numToKeepStr: '5']],
]
def imageName = 'base'

if (!env.CHANGE_ID) {
    if (env.BRANCH_NAME == null) {
        projectProperties.add(pipelineTriggers([cron('H/30 * * * *'), pollSCM('H/5 * * * *')]))
        projectProperties.add(disableConcurrentBuilds())
    }
}

properties(projectProperties)
pipeline{
  agent any
  tools{
    maven 'M3'
   }
  stages{
    stage('git checkout'){
       steps{
	 git 'https://github.com/boomcboom/boom-test-1.git'
	}
    }
    stage('Build'){
       steps{
         sh 'mvn clean compile'
      }
    }
  }	
}
