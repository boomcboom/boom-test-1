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
