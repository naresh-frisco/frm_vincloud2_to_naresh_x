pipeline {
    agent { label "slave1" }
    
    triggers {
        pollSCM('* * * * *')
    }    

    stages {
        stage('clone_project_B why not working') {
            steps {
                echo 'clone_project_B why not working??'
                git branch: 'main', url: 'https://github.com/naresh-frisco/frm_vincloud2_to_naresh_x.git'
            }
        }
        stage('build_project_C') {
            steps {
                echo 'build_projectC'
                sh 'yum install maven -y'
                sh 'mvn -Dmaven.test.failure.ignore=true install'
            }
        } 
        stage('Docker_build  not working???') {
            steps {
                echo 'Docker build_projecte'
                echo 'Tag the Image'
                sh 'docker build -t projecte .' 
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
                sh 'docker tag  projecte nareshfrisco/projecte'
            }
        } 
        stage('Deploy to docker hub') {
            steps {
                echo 'Deploy to docker hub'
                sh 'docker push nareshfrisco/projecte'
            }
        }
        stage('Remove Docker conatiner') {
            steps {
                echo 'Remove Docker conatiner'
                sh 'docker stop projecte_conatiner || true'
                sh 'docker rm projecte_conatiner || true'
            }
        }        
        stage('Run docker image') {
            steps {
                echo 'Deploy to docker hub'
                sh 'docker run --name projecte_conatiner -d -p 8181:8080 nareshfrisco/projecte'
            }
        }
        stage('added one more stage FInally It is working now god is great8') {
            steps {
                echo 'added one more stage'                
            }
        }        
    }
}
