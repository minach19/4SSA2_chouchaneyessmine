pipeline {
    agent any

    tools {
        jdk 'JAVA_HOME'
        maven 'M2_HOME'
    }

    stages {
        stage('Récupération du projet') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/minach19/4SSA2_chouchaneyessmine.git',
                    credentialsId: 'github-credentials'
            }
        }

        stage('Génération du livrable') {
            steps {
                dir('backend') {
                    sh 'mvn clean package -DskipTests'
                }
            }
        }
    }

    post {
        success {
            archiveArtifacts artifacts: 'backend/**/target/*.jar', fingerprint: true
            echo 'Build réussi : le livrable .jar est généré dans target/'
        }
    }
}
