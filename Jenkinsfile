pipeline{
  agent any
  stages{
    stage("Clonnig"){
      steps{
        git 'https://github.com/Hareesha123/pipeline_demo.git'
        eccho "stage completed"
      }
    }
    
    stage("Build stage"){
      parallel{
        stage 1("1st build stage"){
          steps{
            sh 'mvn clean install'
            echo "stahe completed"
          }
        }
        stage 2("2nd build stage"){
          steps{
            sh 'mvn clean install'
            echo "2nd stage build success"
          }
        }
      }
    }
    
    stage("Push to artifact"){
      steps{
        echo "push stage completed"
      }
    }
    
    stage("Testing"){
      parallel{
        stage 1("stage-1 testing"){
          steps{
            echo "testing is done"
          }
        }
        
        stage 2("stage-2 testing"){
          steps{
            echo "testing completed"
          }
        }
      }
    }
    
    stage("Deployment stage"){
      steps{
        sh 'sudo cp /home/ec2-user/jenkins/workspace/pipeline_Jenkinsfile/target/*.war /opt/apache-tomcat-9.0.64/webapps'
        echo "war file deployed"
      }
    }
  }
}
