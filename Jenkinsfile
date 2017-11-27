pipeline {
    agent {
        docker {
            image 'agileek/ionic-framework:latest'
            args '-u root:sudo -v $HOME/bTemp/JenkinsProjects:/myproject'
//            args '-v $HOME/.m2:/myApp:rw'
        }
    }
    stages {
        stage('build') {
            steps {
//                sh 'ionic cordova resources'
                sh 'ionic cordova platform add android'
                sh 'ionic cordova build android'
            }
        }
    }
}
