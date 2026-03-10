pipeline {
    agent any

    environment {
        SF_USERNAME = 'cpgvaluechain2025@gmail.com'
        SF_CLIENT_ID = 's3MVG9kb26yEQGZW2LFMSXmeG_Vt16kYneIG.8IL_HqbPfkzvsrWIIZiEXoKUqac95EVCdCwQZYJBeaQQjSI9p'
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/MohthyJayakrishnan/Jotform-User.git'
            }
        }

        stage('Authenticate Salesforce') {
            steps {
                withCredentials([file(credentialsId: '9e7ff4d9-1675-433d-a8df-411cd7b0f6d8', variable: 'JWT_KEY')]) {
                    sh '''
                    sfdx auth:jwt:grant \
                    --clientid $SF_CLIENT_ID \
                    --jwtkeyfile $JWT_KEY \
                    --username $SF_USERNAME \
                    --instanceurl https://login.salesforce.com
                    '''
                }
            }
        }

        stage('Deploy to Salesforce') {
            steps {
                sh 'sfdx force:source:deploy -p force-app'
            }
        }

    }
}
