pipeline {
  agent {
    kubernetes {
      yaml '''
metadata:
  labels:
    some-label: some-label-value
    class: KubernetesDeclarativeAgentTest
spec:
  containers:
  - name: jnlp
    env:
    - name: CONTAINER_ENV_VAR
      value: jnlp
  - name: docker
  image: docker:rc-windowsservercore-1809
  command:
  - ping
  - localhost
  - -t
  tty: true
'''
    }
  }
  stages {
    stage('Run pls') {
      steps {
        cmd 'set'
        cmd "echo OUTSIDE_CONTAINER_ENV_VAR = ${CONTAINER_ENV_VAR}"
        container('jnlp') {
          cmd 'echo MAVEN_CONTAINER_ENV_VAR = ${CONTAINER_ENV_VAR}'
          cmd 'mvn -version'
        }
        container('docker') {
          powershell.exe 'docker build . -t aspire.io/rct-automation:0.0.1 -o type=tar,dest="C:\\Users\\mihailo.plavsic\\Documents\\rct-automation.tar"'
        }
      }
    }
  }
}