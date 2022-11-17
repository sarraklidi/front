pipeline {
    agent any

    tools {
        nodejs 'NODE_HOME'
    }
    
stages {
    stage('Getting project from Github') {
            steps {
                git branch : 'main' ,
                url: 'https://github.com/sarraklidi/front.git',
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
                sh 'docker build -t sarraklidi/achat_frontf .'
            }
        }
        stage('Docker login')
        {
            steps {
		   
		    sh '''
		    echo $dockerhub_PSW | docker login -u sarraklidi -p dckr_pat_os789gFKgYlRvT9wPzplzmIlttk
		    docker push sarraklidi/achat_frontf 
		    '''
            }    
       
        }
    
    }
}
