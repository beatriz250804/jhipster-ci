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
        bat './mvnw -B -DskipTests=false clean package'
      }
    }

    stage('Unit tests') {
      steps {
        bat './mvnw -B test'
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

