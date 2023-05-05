pipeline{

/*   agent {
      kubernetes {
        yamlFile 'pod.yaml'
  }
  } */

  agent { label 'docker' }

  stages {
    stage('Checkout Source') {
      steps {
        git 'https://github.com/MihailoP34/playjenkins.git'
      }
    }

    stage('Init'){
      steps{
        container('docker-cli'){
          powershell.exe "Started docker agent"
        }
      }
    }
    stage('Build'){
      steps{
        powershell.exe """ docker build . -t aspire.io/rct-automation:0.0.1 -o type=tar,dest="C:\\Users\\mihailo.plavsic\\Documents\\rct-automation.tar" """
      }
    }

  }
}