pipeline {
  agent {
    kubernetes {
      yaml '''
metadata:
  labels:
    class: KubernetesDeclarativeAgentTest
spec:
  nodeSelector:
      kubernetes.io/os: windows
  containers:
  - name: jnlp
    image: jenkins/inbound-agent:nanoserver-1809
    tty: true
  - name: docker-cli
    image: docker:rc-windowsservercore-1809
    cmd:
    - ping
    - localhost
    - -t
    tty: true
    securityContext:
      privileged: true
    env:
    - name: CONTAINER_ENV_VAR
      value: docker
'''
    }
  }
    stages {
      stage('Run pls') {
        steps {
          powershell HOSTNAME
          container('docker-cli') {
            powershell ' docker build . -t aspire.io/rct-automation:0.0.1 -o type=tar,dest="C:\\Users\\mihailo.plavsic\\Documents\\rct-automation.tar" '
          }
        }
      }
    }
}