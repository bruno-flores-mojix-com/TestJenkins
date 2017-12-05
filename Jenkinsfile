pipeline {
  agent {
    node {
      label 'master'
    }
    
  }
  stages {
    stage('setup_env') {
      steps {
        sh 'echo "We should do something like: apt-get update -y"'
      }
    }
    stage('install_dependencies') {
      steps {
        sh 'npm install'
        tool 'NPM'
      }
    }
    stage('build_android_application') {
      steps {
        sh 'ionic cordova platform add android'
        sh 'ionic cordova build android'
      }
    }
    stage('install_application') {
      steps {
        sh 'echo "Should install to some device"'
      }
    }
    stage('test') {
      steps {
        sh 'echo "do some test here"'
      }
    }
    stage('Deliver') {
      steps {
        sh 'echo "Steps before deliver, ex.: ./jenkins/scripts/deliver.sh"'
        input 'Finished using the web site? (Click "Proceed" to continue)'
        sh 'echo "Steps to upload the file at: ./jenkins/scripts/kill.sh"'
      }
    }
  }
  environment {
    CI = 'true'
  }
  post {
    success {
      echo 'Do something when it is successful'
      slackSend(color: 'good', message: 'Build Complete!')
      
    }
    
    failure {
      echo 'Do something when it is failed'
      slackSend(color: '#c64211', message: 'There are errors on the build, please review it.')
      
    }
    
  }
}