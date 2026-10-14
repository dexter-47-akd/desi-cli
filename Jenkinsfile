pipeline {
    agent any
    triggers {
        cron('H 2 * * *')  // Daily ~2 AM (H = hash-based load balancing)
        cron('H */4 * * *')  // Every 4 hours
         cron('H 0 * * 0')    // Weekly Sunday midnight
    }
    stages {
        stage('Build') { steps { sh './build.sh' } }
    }
}
