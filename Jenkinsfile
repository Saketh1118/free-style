pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                script {
                    // Clean workspace before cloning
                    deleteDir()
                    
                    // Clone the repository
                    git 'https://github.com/your-username/your-repository.git'
                }
            }
        }

        stage('Build') {
            steps {
                // Your build steps here
                sh 'mvn clean install'  // Replace with your build command
            }
        }

        stage('Deploy to Main') {
            when {
                expression { BRANCH_NAME == 'main' }
            }
            steps {
                // Your deployment steps for main branch
                sh 'echo "Deploying to production"'
            }
        }

        stage('Deploy to Develop') {
            when {
                expression { BRANCH_NAME == 'develop' }
            }
            steps {
                // Your deployment steps for develop branch
                sh 'echo "Deploying to staging"'
            }
        }
    }

    post {
        always {
            // Cleanup steps, if needed
        }
    }
}
