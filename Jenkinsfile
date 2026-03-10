pipeline {
    agent any

    environment {
        SF_USERNAME = 'cpgvaluechain2025@gmail.com'
        SF_CLIENT_ID = '3MVG9kb26yEQGZW2LFMSXmeG_Vt16kYneIG.8IL_HqbPfkzvsrWIIZiEXoKUqac95EVCdCwQZYJBeaQQjSI9p'
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/MohthyJayakrishnan/Jotform-User.git'
            }
        }

        stage('Authenticate Salesforce') {
            steps {
                bat """
                "C:\\Program Files\\sf\\bin\\sf.cmd" org login jwt ^
                --client-id %SF_CLIENT_ID% ^
                --jwt-key-file C:\\salesforce-jwt\\server.key ^
                --username %SF_USERNAME% ^
                --instance-url https://login.salesforce.com ^
                --alias cpgvalue
                """
            }
        }

        stage('Deploy to Salesforce') {
            steps {
                bat '"C:\\Program Files\\sf\\bin\\sf.cmd" project deploy start --source-dir force-app --target-org cpgvalue'
            }
        }

    }
}
