# 💫 About Me:
# SLACK-INTEGRATION
blog of integrate jenkins

# 💫 About Me:


STEP-1 ==> CREATE CHANNEL WITH SLACK NOTIFICATION

STEP-2 ==> GO TO THAT CHANNEL DETAILS WITH RIGHT CLICK OF THAT CHANNEL ALREADY CREATED

STEP-3 ==> SELECT JENKINS CI AND GENERATED TOCKEN 

STEP-4 ==> GOTO JENKINS CONFIGURATION OF Slack Workspace " ADD == DEFAULT NAME GENERATED NAME IN SLACK APP DIRECTORY ++++++ EAXMPLE ---- > "devops-proworkspace" INSTEAD OF USE devops-pro  <----- CHANNEL NAME

STEP-5 ==> CONFIGURE WITH TOCKENS AND SET UP ALL

STEP-6 ==> TEST THIS " SUCCESS / FAIL "

STEP-7 ==> ADD THIS BELOW DEFAULT SLACK NOTIFICAION SCRIPT INTO YOUR PIPELINE " "

🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃🢃

#
// First, you need to install the Slack plugin on your Jenkins instance.
// author "saroj_ekka"
// Define the Slack channel to which you want to send the notification.
def slackChannel = '#devops_project' <--------------------------------------------------" change your channel name"

// Define the Jenkins pipeline.
pipeline {
    agent any

    stages {
        stage('CHECKOUT') {
            steps {
                git 'https://github.com/ekka007/star-agile-project-demo.git'
            }
        }
        stage('CODE-BUILD') {
            steps {
                sh 'mvn compile'
            }
        }
    }
    post {
        success {
            // Send a notification to Slack when the build is successful.
            slackSend color: '#00FF00', message: "Build completed successfully!", channel: slackChannel
        }
        failure {
            // Send a notification to Slack when the build fails.
            slackSend color: '#FF0000', message: "Build failed!", channel: slackChannel
        }
    }
}
#

