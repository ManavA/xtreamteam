#!groovy

pipeline {
 agent any
  tools {
        //env.M2_HOME = tool name: 'Maven 3.2', type: 'maven'
        maven 'Maven3.6.3'
        }
       
  stages{
       
        stage('SFDA Workflow Engine Code Checkout') {
            steps {
                echo "Cleaning workspace before checkout"  
                cleanWs()
                git branch: "main", credentialsId: 'sfdaPipe', url: 'https://github.com/jcvalladares/xtreamteam.git'
            }
        }
       
       
        stage('Code Build and Unit Test suite') {
            steps {
                script {    
                        sh "${env.M2_HOME}/bin/mvn -f ${env.WORKSPACE}/sfda/pom.xml clean install"
                }

            }
        }

      }
     
}
