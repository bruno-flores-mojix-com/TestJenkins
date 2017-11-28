pipeline {
    agent {
        docker {
            image 'agileek/ionic-framework:latest'
        }
    }
    stages {
        stage('build') {
            steps {
//                sh 'ionic cordova resources'
                sh 'npm install'
                sh 'ionic cordova platform add android'
                sh 'ionic cordova build android'
            }
        }
    }
}
