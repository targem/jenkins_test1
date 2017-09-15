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
    stage('build_pc') {
      steps {
        parallel(
          "build_pc": {
            timeout(unit: 'MINUTES', time: 6) {
              isUnix()
              sh 'echo "it is unix"'
            }
            
            
          },
          "build_linux": {
            echo 'building linux'
            
          },
          "build mac": {
            echo 'building mac'
            
          }
        )
      }
    }
    stage('deploy') {
      steps {
        timeout(time: 30) {
          node(label: 'versions') {
            dir(path: '${versions_path}')
          }
          
        }
        
        echo 'deploing all'
      }
    }
  }
}