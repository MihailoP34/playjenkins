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