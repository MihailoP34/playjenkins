pipeline{
  stages{
    stage('Run pls') {

      steps{
        
        podTemplate{
          node(POD_LABEL){
            container('dind'){
              bat 'dir'
              powershell ' docker build . -t aspire.io/rct-automation:0.0.1 -o type=tar,dest="C:\\Users\\mihailo.plavsic\\Documents\\rct-automation.tar" '
            }
          }
        }

      }

    }
  }
}