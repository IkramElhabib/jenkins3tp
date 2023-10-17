pipeline {
  agent any
  tools {
    maven 'maven'
  }
  stages {
    stage ("Clean up"){
      steps {
        deleteDir()
      }
    }
    stage ("Clone repo"){
      steps {
        sh "git clone https://github.com/IkramElhabib/jenkins3tp.git"
      }
    }
    stage("Generate backend image") {
    steps {
        dir("jenkins3tp") {
            sh "mvn clean install"
            sh "docker build -t backend ."
        }
    }
}
stage("Run docker compose") {
    steps {
        dir("jenkins3tp") {
            sh "docker-compose up -d"
        }
    }
}
}
}
