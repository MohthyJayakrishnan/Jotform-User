pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/MohthyJayakrishnan/Jotform-User.git'
            }
        }

        stage('Authenticate Salesforce') {
            steps {
                bat '"C:\\Program Files\\sf\\bin\\sf.cmd" org login jwt --client-id YOUR_CLIENT_ID --jwt-key-file C:\\salesforce-jwt\\server.key --username cpgvaluechain2025@gmail.com --alias cpgvalue --instance-url https://login.salesforce.com'
            }
        }

        stage('Verify Org Connection') {
            steps {
                bat '"C:\\Program Files\\sf\\bin\\sf.cmd" org list'
            }
        }

        stage('Deploy to Salesforce') {
            steps {
                bat '"C:\\Program Files\\sf\\bin\\sf.cmd" project deploy start --source-dir force-app --target-org cpgvalue'
            }
        }
    }
}
