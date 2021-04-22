pipeline{
    tools{
        jdk 'JAVA_HOME'
        maven 'M2_HOME'
    }
    agent none
      stages{
          stage('Checkout'){
              agent any
              steps{
                  git 'https://github.com/Sathishdevops38/game-of-life-.git'
              }
          }
          stage('Compile'){
              agent any
              steps{
                  sh 'mvn compile'
              }
          }
          stage('UnitTest'){
              agent{label 'linux_slave'}
              steps{
                  git 'https://github.com/devops-trainer/game-of-life.git'
                  sh 'mvn test'
              }
              post{
                  always{
                      junit 'gameoflife-web/target/surefire-reports/*.xml'
                  }
              }
          }
          stage('Package'){
              agent any
              steps{
                  sh 'mvn package'
              }
          }
         
      }
    
}
