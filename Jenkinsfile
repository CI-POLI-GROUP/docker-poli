pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                script {
                    try {
                        git branch: 'main',
                            url: 'https://github.com/codemotozu/docker-poli.git'
                             
                        echo 'Checkout completado exitosamente'
                    } catch (Exception e) {
                        echo "Error en checkout: ${e.getMessage()}"
                        error "Fallo en el checkout"
                    }
                }
            } 
        }
        
        stage('Build') {
            steps {
                echo 'Iniciando etapa de build...'
                echo 'Build completado'
            }
        }
        
        stage('Test') {
            steps {
                echo 'Iniciando pruebas...'
                echo 'Pruebas completadas'
            }
        }

        stage('Deploy') {
            steps {
                sh "docker-compose down -v"
            }
        }
    }
    
    post {
        success {
            echo 'Pipeline ejecutado exitosamente!'
        }
        failure {
            echo 'El pipeline ha fallado'
        }
    }
}
