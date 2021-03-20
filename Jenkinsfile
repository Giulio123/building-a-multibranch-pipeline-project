pipeline {
     agent any
     stages {
         stage('Build') {
             steps {
                 echo 'Building...'
             }
             post {
                 always {
                     jiraSendBuildInfo site: 'sugfdo.atlassian.net'
                 }
             }
         }
         stage('Deploy - Staging') {
             when {
                 branch 'JJ-4_try-deploy'
             }
             steps {
                 echo 'Deploying to Staging from JJ-4_try-deploy...'
             }
             post {
                 always {
                     jiraSendDeploymentInfo site: 'sugfdo.atlassian.net', environmentId: 'us-stg-1', environmentName: 'us-stg-1', environmentType: 'staging'
                 }
             }
         }
         stage('Deploy - Production') {
            when {
                branch 'JJ-4_try-deploy'
            }
            steps {
                echo 'Deploying to Production from JJ-4_try-deploy...'
            }
            post {
                always {
                    jiraSendDeploymentInfo site: 'sugfdo.atlassian.net', environmentId: 'us-prod-1', environmentName: 'us-prod-1', environmentType: 'production'
                    jiraSendDeploymentInfo site: 'sugfdo.atlassian.net', environmentId: 'us-prod-1', environmentName: 'us-prod-1', environmentType: 'production'
                }
            }
         }
     }
 }