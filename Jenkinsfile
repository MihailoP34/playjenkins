pipeline{

podTemplate(yaml: '''
    apiVersion: v1
    kind: Pod
    spec:
      containers:
      - name: docker
        image: docker:rc-windowsservercore-1809
        command:
        - ping
        args:
        - localhost
        - -t
''') {
  node(POD_LABEL) {
    stage('Pls work') {
        git 'https://github.com/MihailoP34/playjenkins.git'
      container('docker') {
        stage('Try build') {
          powershell.exe 'docker build . -t aspire.io/rct-automation:0.0.1 -o type=tar,dest="C:\\Users\\mihailo.plavsic\\Documents\\rct-automation.tar"'
        }
      }
    }

  }
}

}