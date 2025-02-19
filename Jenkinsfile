pipeline { 
    agent any
    stages { 
        stage('Checkout') { 
            steps { 
                git branch: 'main', url: 'https://github.com/ajifatu/CICD_go_to_pipeline.git' 
            } 
        } 
 
        stage('Install Dependencies') { 
            steps { 
                sh 'python -m venv venv' 
            } 
        }

        stage('Run Script') { 
            steps { 
                sh './venv/bin/python main.py' 
 
            } 
        } 
    } 

    post { 
    success { 
        emailext subject: "Build SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                 body: "Le build de ${env.JOB_NAME} a réussi.\nConsultez les logs ici: ${env.BUILD_URL}",
                 recipientProviders: [[$class: 'DevelopersRecipientProvider']],
                 to: 'votre-adresse-email@gmail.com'
    } 
    failure { 
        emailext subject: "Build FAILURE: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                 body: "Le build de ${env.JOB_NAME} a échoué.\nConsultez les logs ici: ${env.BUILD_URL}",
                 recipientProviders: [[$class: 'DevelopersRecipientProvider']],
                 to: 'votre-adresse-email@gmail.com'
    } 
}