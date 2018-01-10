node() {
    sh ' git rev-parse --verify HEAD > jenkins_pipeline_output.tmp'
    def commitHash = readFile( 'jenkins_pipeline_output.tmp').split("\r?\n")[0]
    env.GIT_COMMIT = commitHash
    environment {
        PATH = '/Users/admin/Library/Android/sdk/platform-tools:/Users/admin/Library/Android/sdk/tools'
    }
  nvm(nvmInstallURL: 'https://raw.githubusercontent.com/creationix/nvm/v0.33.2/install.sh', nvmIoJsOrgMirror: 'https://iojs.org/dist', nvmNodeJsOrgMirror: 'https://nodejs.org/dist', version: '6.11.3') {
    stage('Installing dependencies') {
      sh 'npm install -g ionic'
      sh 'npm install -g cordova'
      sh 'npm install -g ios-sim ios-deploy'
    }
    stage('build cxi library') {
      // some block
      // sh 'nvm install 6.11.3'
      // sh 'cd subdir1'
        sh 'npm install @angular/http --save'
        sh 'npm install @ionic/storage  --save'
        // sh 'npm install ng2-interceptors --save'
        sh 'npm install'
        sh 'npm run build'
        // sh 'cd dist'
        // sh 'npm link'
        // sh 'cd ../../'
      }


      stage("Prepare") {
              // writeFile file: 'www/fhconfig.json', text: params.FH_CONFIG_CONTENT
              // sh 'rm -rf node_modules'
              sh 'npm install'
              sh "ionic cordova platform rm android"
              sh "ionic cordova platform rm ios"
              sh "ionic cordova platform add android"
              sh "ionic cordova prepare android"
              sh "ionic cordova platform add ios"
              sh "ionic cordova prepare ios"
          //    sh 'npm link @cxi/rest-client'
          }

      stage ("build") {
      sh 'ionic cordova build android'
      sh 'ionic cordova build ios'
      }

      stage ("sign") {
      // add the signing for ios
      // sign release for the application
      }

      stage ("archive")  {
        // archive android
        archiveArtifacts artifacts: "platforms/android/build/outputs/apk/android-debug.apk", excludes: 'platforms/android/build/outputs/apk/*-unaligned.apk'
        // in next term will archive ios
      }
  }
}
