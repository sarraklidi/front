pipeline {
    agent any

    tools {
        nodejs 'NODE_HOME'
    }
    
stages {
    stage('Getting project from Github') {
            steps {
                git branch : 'main' ,
                git branch: 'main', url: 'https://github.com/GhaithBh/front.git',
                credentialsId:"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";
            }
        }
        stage('Install') {
            steps { 
                sh 'npm install'
            }
        }
        stage('Build') {
          steps { 
              sh 'npm run build'
              }
        }
        
        stage ('Build our image'){
            steps{
                sh 'docker build -t ghaithbhs/achat_frontf .'
            }
        }
        stage('Docker login')
        {
            steps {
                sh 'echo $dockerhub_PSW | docker login -u ghaithbhs -p dckr_pat_PvFfLE0rm--tKJiRL1igKeLc2fQ'
            }    
       
        }
      stage('Push') {

			steps {
				sh 'docker push ghaithbhs/achat_frontf'
			}
		}
    }
}
