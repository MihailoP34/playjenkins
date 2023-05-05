agent {
    kubernetes {
        defaultContainer 'docker'
        yaml '''
kind: Pod
spec:
  containers:
  - name: docer-cli
    image: docker:rc-windowsservercore-1809
    command:
    - powershell.exe
    args:
    - ping
    - localhost
    - -t
'''
   }
   stages {
    stage('Init'){
      steps{
        powershell.exe "Started docker agent"
      }
    }

   stages {
    stage('Build'){
      steps{
        powershell.exe """ docker build . -t aspire.io/rct-automation:0.0.1 -o type=tar,dest="C:\\Users\\mihailo.plavsic\\Documents\\rct-automation.tar" """
      }
    }

   }
}