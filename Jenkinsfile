pipeline{
  agent any
  tools {
    maven 'maven'
  }
  stages {
    stage ("clean up"){
      steps {
        deleteDir()
      }
    }
    stage ("clone ropo"){
      steps {
        sh "git clone https://github.com/souleymenBS/back-spring.git"
      }
    }
    stage ("generate backend image") {
      steps {
        dir("backend"){
          sh "mvn clean install"
          sh "docker build -t backend ."
        }
      }
    }
    stage ("run docker compose") { 
      steps {
        dir("backend"){
          sh " docker compose up -d"
        }
      }
    }
  }
}
      
