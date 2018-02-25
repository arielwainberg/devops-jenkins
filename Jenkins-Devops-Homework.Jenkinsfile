pipeline {

    agent any
    parameters {
        string(name: 'EmailAdress', defaultValue: 'ariel@xxxxx.co.il', description: 'Notification Email Address')
    }
    stages {
        stage('Step-1: Hello_World') {
            steps {
                sh "echo 'Hello Wolrd'"
            }
        }
        stage ('Step-2: Jenkins_was_here') {
            steps{
                sh "date >> /tmp/jenkins_was_here"
            }
        }
    }
    post {
        success {
            mail (to: "${params.EmailAdress}", subject: "Job '${env.JOB_NAME}' Build(#${env.BUILD_NUMBER}) Succeded" , body: "Job:'${env.JOB_NAME}' on Build:(#${env.BUILD_NUMBER}) Succesesfully ran.")
        }
        failure {
            mail (to: "${params.EmailAdress}", subject: "Job '${env.JOB_NAME}' Build(#${env.BUILD_NUMBER}) Failed" , body: " Job:'${env.JOB_NAME}' on Build:(#${env.BUILD_NUMBER}) Failed To run, go back to Debug!")
        }
    }
}