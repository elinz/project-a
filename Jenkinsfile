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
        dir(path: 'icap-data') {
          git(url: 'https://github.com/elinz/project-b', branch: 'dev', credentialsId: 'elinz')
        }

      }
    }
    stage('Copy files') {
      steps {
        bat 'xcopy %WORKSPACE%\\FolderA\\*.* %DESTINATION_FOLDER%\\%BUILD_NUMBER%\\FolderA\\*.* /S /H'
        bat 'xcopy %WORKSPACE%\\FolderB\\*.* %DESTINATION_FOLDER%\\%BUILD_NUMBER%\\FolderB\\*.* /S /H'
        bat 'xcopy %WORKSPACE%\\icap-data\\Folder\\*.* %DESTINATION_FOLDER%\\%BUILD_NUMBER%\\icap-data\\Folder\\*.* /S /H'
      }
    }
  }
  environment {
    DESTINATION_FOLDER = '\\\\redarchive2\\disl\\Development\\Jenkins\\EricPlayground\\EricMultipleReposTest'
  }
}