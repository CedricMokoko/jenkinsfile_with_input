pipeline{
  agent any

  // options{
    // parallelAlwaysFailFast()
  // }

  stages{

    stage('application build'){
      failFast true

      parallel{
        stage('build frontend'){
          steps{
            echo "Build frontend ..."
          }
        }

        stage('build backend'){
          steps{
            echo "Build backend ..."
          }
        }
      }
    }
    
    
    stage('tests'){
      steps{
        echo "Exécution tests ..."
      }
    }

    stage('deployment'){
      input{
        message 'Voulez vous deployer en production?'
        ok 'deployer!'
        submitter 'admin, devops'
        submitterParameter 'USER_SUBMIT'
        parameters{
          string(name: 'VERSION', defaultValue: 'latest', description: 'la version déployée')
        }
      }

      steps{
        echo "USER_SUBMIT: ${USER_SUBMIT}"
        echo "VERSION: ${VERSION}"
        echo "Deploy application ..."
      }
    }

  }
}