pipeline{
  agent any

  stages{
    stage('build'){
      steps{
        echo "Build application ..."
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
        submitParameter 'USER_SUBMIT'
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