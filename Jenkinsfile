pipeline {
  agent any

  environment {
    MAVEN_OPTS = "-Xmx1024m"
  }

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Build') {
      steps {
        sh './mvnw -B -DskipTests=false clean package'
      }
    }

    stage('Unit tests') {
      steps {
        sh './mvnw -B test'
      }
    }
  }

  post {
    success {
      echo "✅ Build correcto"
    }
    failure {
      echo "❌ Falló el pipeline"
    }
  }
}

