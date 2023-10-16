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
        dir("back-spring"){
          sh "mvn clean install"
          sh "docker build -t backend ."
        }
      }
    }
    stage ("run docker compose") { 
      steps {
        dir("back-spring"){
          sh "sudo docker compose up -d -S "
        }
      }
    }
  }
}
      
