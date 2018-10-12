pipeline {
  agent {
    node {
      label 'ArcGISPro2.2'
    }

  }
  stages {
    stage('Copy repos') {
      steps {
        git(url: 'https://github.com/elinz/project-a', branch: 'dev', credentialsId: 'elinz')
        git(url: 'https://github.com/elinz/project-b', branch: 'dev', credentialsId: 'elinz')
      }
    }
    stage('Copy files') {
      steps {
        bat 'xcopy %WORKSPACE%\\*.* %DESTINATION_FOLDER%\\%BUILD_NUMBER%\\*.* /S /H'
      }
    }
  }
  environment {
    DESTINATION_FOLDER = '\\\\redarchive2\\disl\\Development\\Jenkins\\EricPlayground\\EricMultipleReposTest'
  }
}