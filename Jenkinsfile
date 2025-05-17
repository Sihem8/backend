pipeline { 
    agent any 
    tools {
        maven 'naven' 
    }

    stages { 
        stage("Clean up") { 
            steps { 
                deleteDir() 
            }  
        } 

        stage("Clone repo") { 
            steps {
                sh "git clone https://github.com/MaBouz/backend.git" 
            } 
        }

        stage("Generate backend image") { 
            steps {
                dir("backend") { 
                    sh "mvn clean install" 
                    sh "docker build -t backend ."
                }
            }
        } 

        stage("Run docker compose") {  
            steps { 
                dir("backend") { 
                    sh "docker compose up -d" 
                } 
            } 
        } 
    } 
}
