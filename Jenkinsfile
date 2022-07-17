pipeline{
  agent any
  stages{
    stage("Clonnig"){
      steps{
        git 'https://github.com/Hareesha123/pipeline_demo.git'
        echo "stage completed"
      }
    }
    
    stage("Build stage"){
      parallel{
        stage("stage-1 build"){
          steps{
            sh 'mvn clean install'
            echo "1st stage completed"
          }
        }
        stage("stage-2 build"){
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
        stage("stage-1 testing"){
          steps{
            echo "testing is done"
          }
        }
        
        stage("stage-2 testing"){
          steps{
            echo "testing completed"
          }
        }
      }
    }
    
    stage("Deployment stage"){
      steps{
        sh 'sudo cp /home/ec2-user/jenkins/workspace/pipeline_jenkinsfile/webapp/target/*.war /opt/apache-tomcat-9.0.64/webapps'
        echo "war file deployed"
      }
    }
  }
}
