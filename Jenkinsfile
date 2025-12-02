pipeline {
  agent any

  tools {
    jdk 'Java11'      // اسم JDK كما ستسجله في Jenkins Global Tools
    maven 'Maven3'    // اسم Maven كما ستسجله في Jenkins
  }

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/<YOUR_USERNAME>/<REPO>.git'
      }
    }

    stage('Build') {
      steps {
        sh 'mvn -B clean package'   // -B batch mode مناسب لــ CI
      }
    }

    stage('Test') {
      steps {
        sh 'mvn test'
      }
    }

    stage('Archive') {
      steps {
        archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
      }
    }
  }

  post {
    success {
      echo "Pipeline succeeded"
    }
    failure {
      echo "Pipeline failed"
    }
  }
}

