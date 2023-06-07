pipeline {
    agent any
    environment {
    PATH='/usr/local/bin:/usr/bin:/bin'
}
    stages {
       stage('NPM Setup') {
          steps {
          sh 'npm install'
         }
       }
        
      stage('Starting PM2 Server') {
         steps {
          sh 'pm2 start index.js'
        }
       }
      
 }
}
