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
    securityContext:
      privileged: true
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

    stage('Checkout Source') {
      steps {
        git 'https://github.com/MihailoP34/playjenkins.git'
      }
    }
      stage('Run pls') {
        steps {
          container('docker-cli') {
            powershell ' docker build . -t aspire.io/rct-automation:0.0.1 -o type=tar,dest="C:\\Users\\mihailo.plavsic\\Documents\\rct-automation.tar" '
          }
        }
      }
    }
}