pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/MohthyJayakrishnan/Jotform-User.git'
            }
        }

        stage('Check Salesforce CLI') {
            steps {
                bat '"C:\\Program Files\\sf\\bin\\sf.cmd" --version'
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
