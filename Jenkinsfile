pipeline{
  agent{
    kubernetes{
      podTemplate {
        node(POD_LABEL) {
          stages {
            stage('Run pls') {
              steps {
                container('dind') {
                  powershell ' docker build . -t aspire.io/rct-automation:0.0.1 -o type=tar,dest="C:\\Users\\mihailo.plavsic\\Documents\\rct-automation.tar" '
                }
              }
            }
          }
        }
      }
    } 
  }
}