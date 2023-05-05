pipeline{

  agent {
      kubernetes {
        yamlFile 'yaml'
          yaml '''
  kind: Pod
  spec:
    containers:
    - name: docker-cli
      image: docker:rc-windowsservercore-1809
      command:
      - powershell.exe
      args:
      - ping
      - localhost
      - -t
  '''
  }
  }

  stages {
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