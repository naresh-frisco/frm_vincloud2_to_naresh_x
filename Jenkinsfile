pipeline {
    agent { label "slave1" }
    
    triggers {
        pollSCM('* * * * *')
    }    

    stages {
        stage('clone_project_B') {
            steps {
                echo 'clone project B'
                git 'https://github.com/naresh-frisco/frm_vincloud2_to_naresh_x.git'
            }
        }
        stage('build_project_B') {
            steps {
                echo 'build_projectB'
                sh 'yum install maven -y'
                sh 'mvn -Dmaven.test.failure.ignore=true install'
            }
        } 
        stage('Docker_build') {
            steps {
                echo 'Docker build_projectd'
                sh 'docker build -t projectd .' 
            }
        }
        stage('login to dockerhub') {
            steps {
                echo 'login to dockerhub'
                sh 'docker login -u nareshfrisco -p MankPrb8Great$'
            }
        } 
        stage('Tag the Image') {
            steps {
                echo 'Tag the Image'
                sh 'docker tag  projectd nareshfrsico/projectd'
            }
        } 
        stage('Deploy to docker hub') {
            steps {
                echo 'Deploy to docker hub'
                sh 'docker push nareshfrisco/projectd'
            }
        }
        stage('Remove Docker conatiner') {
            steps {
                echo 'Remove Docker conatiner'
                sh 'docker stop projectd_conatiner || true'
                sh 'docker rm projectd_conatiner || true'
            }
        }        
        stage('Run docker image') {
            steps {
                echo 'Deploy to docker hub'
                sh 'docker run --name projectd_conatiner -d -p 8181:8080 nareshfrisco/projectd'
            }
        }
        stage('added one more stage') {
            steps {
                echo 'added one more stage'                
            }
        }        
    }
}
