pipeline {

    agent any

    stages {

      stage("Build stencil") {
        // when {
        //   changeset "**/stencil-library/*.*"
        //   beforeAgent true
        // }
        steps {
          dir('stencil-library') {
            bat 'del /Q node_modules'
            bat 'del /Q package-lock.json'
            bat 'npm install'
            bat 'npm run build-prod'
            bat 'npm link'
          }
        }
      }
      
      stage("Build react") {
        // when {
        //   changeset "**/my-app/*.*"
        //   beforeAgent true
        // }
        steps {
          dir('my-app') {
            bat 'del /Q node_modules'
            bat 'del /Q package-lock.json'
            bat 'npm install'
            bat 'npm link stencil-library-demo-npm'
            bat 'npm run build'
            bat 'npm pack'
          }
        }
      }
    }
}