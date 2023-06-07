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
        
   stage('Sonarqube') {
    environment {
        scannerHome = tool 'SAST-APPSEC'
    }
    steps {
        withSonarQubeEnv('SonarQubeServer') {
            sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=Zensar-Seat-Booking-Banglore-NodeJS -Dsonar.sources=."
        }
        timeout(time: 10, unit: 'MINUTES') {
            waitForQualityGate abortPipeline: true
        }
    }
}
      
 }
}
