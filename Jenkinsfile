pipeline{
  agent any
  
    stages{
      stage('Checkout'){
        steps{
          echo 'Pulling code from Github'
          checkout scm
        }
      }
      stage('Build'){
        step{
          echo 'Building project is going on'
          bat 'echo Build completed succesfully!'
        }
      }
      stage('Validation Check'){
        steps{
          echo 'Validating project readiness'
          bat '''
          findstr READY=true check.txt > nul
          if errorlevel 1 (
            echo Validation Failure
            exit 1
          )else(
            echo Validation passed
          )
          '''
        }
      }
      stage('Manager Approval'){}
      steps{
        input message:'Approve deployement?',ok:'Approve'
        
      }
    }
  stage('Ready for deployement'){
    steps{
      echo 'Deployed approved and ready'
    } 
  }
}
