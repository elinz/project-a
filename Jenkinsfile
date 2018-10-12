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
        bat 'xcopy %WORKSPACE%\\MyFolderA\\*.* %DESTINATION_FOLDER%\\%BUILD_NUMBER%\\MyFolderA\\*.* /S /H'
        bat 'xcopy %WORKSPACE%\\MyFolderB\\*.* %DESTINATION_FOLDER%\\%BUILD_NUMBER%\\MyFolderB\\*.* /S /H'
        bat 'xcopy %WORKSPACE%\\icap-data\\Folder\\*.* %DESTINATION_FOLDER%\\%BUILD_NUMBER%\\icap-data\\Folder\\*.* /S /H'
      }
    }
    stage('Delete workspace') {
      steps {
        cleanWs(cleanWhenAborted: true, cleanWhenFailure: true, cleanWhenNotBuilt: true, cleanWhenSuccess: true, cleanWhenUnstable: true, cleanupMatrixParent: true, deleteDirs: true)
      }
    }
  }
  environment {
    DESTINATION_FOLDER = '\\\\redarchive2\\disl\\Development\\Jenkins\\EricPlayground\\EricMultipleReposTest'
  }
}