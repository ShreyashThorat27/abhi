pipeline {
    agent any
    stages {
        stage ('SCM Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/ShreyashThorat27/abhi.git'
        
            }
        }
        
        stage ('docker image build') {
            steps {
                sh '/usr/bin/docker build -t shreyash27/myweb .'    
            }
        }
        
        stage ('docker login') {
            steps {
                sh 'echo  | /usr/bin/docker login -u shreyash27 --password-stdin'
            }
        }
        
        stage ('docker push') {
            
            steps {
                sh '/usr/bin/docker image push shreyash27/myweb'
            }
        }
        
        stage ('user input') {
            
            steps {
                input 'Are you sure? You want to deploy.'
            }
        }
        
        stage ('existings service remove') {
            steps {
                sh '/usr/bin/docker service rm myweb'
            }
        }
        
        stage ('start sevice') {
            steps {
                sh '/usr/bin/docker service create --name myweb -p 9000:80 --replicas 2 shreyash27/myweb'
            }
        }
        
        
    }
    
}
