pipeline {
  agent {
    node {
      label '"master"'
    }
    
  }
  stages {
    stage('preparings') {
      steps {
        echo '"getting stuff"'
      }
    }
    stage('buildJu') {
      steps {
        script {
          agent {
            label "docker"
            docker { image 'registry.targem.ru/node6:latest' }
            reuseNode true
          }
          steps {
            sh 'pwd; ls -alF; hostname'
          }
        }
        
      }
    }
  }
}