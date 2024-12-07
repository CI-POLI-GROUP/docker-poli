// Pipeline declarativo de Jenkins que define un flujo automatizado de CI/CD
pipeline {
    // Especifica que este pipeline puede correr en cualquier agente disponible de Jenkins
    agent any
    
    // Define las diferentes etapas del pipeline
    stages {
        // Etapa de Checkout: Obtiene el código fuente del repositorio
        stage('Checkout') {
            steps {
                // Usa un bloque script para ejecutar código groovy más complejo
                script {
                    try {
                        // Clona el repositorio Git, especificando la rama 'main'
                        git branch: 'main',
                            url: 'https://github.com/codemotozu/docker-poli.git'
                             
                        // Mensaje de éxito si el checkout se completa
                        echo 'Checkout completado exitosamente'
                    } catch (Exception e) {
                        // Manejo de errores: muestra el mensaje de error y falla el pipeline
                        echo "Error en checkout: ${e.getMessage()}"
                        error "Fallo en el checkout"
                    }
                }
            } 
        }
        
        // Etapa de Build: Aquí iría la construcción del proyecto
        // Actualmente solo tiene mensajes de placeholder
        stage('Build') {
            steps {
                echo 'Iniciando etapa de build...'
                echo 'Build completado'
            }
        }
        
        // Etapa de Test: Destinada a ejecutar pruebas
        // Actualmente solo tiene mensajes de placeholder
        stage('Test') {
            steps {
                echo 'Iniciando pruebas...'
                echo 'Pruebas completadas'
            }
        }

        // Etapa de Deploy: Maneja el despliegue de la aplicación
        stage('Deploy') {
            steps {
                // Ejecuta docker-compose down con la bandera -v para eliminar volúmenes
                sh "docker-compose down -v"
            }
        }
    }
    
    // Sección post: Define acciones a ejecutar después de que termine el pipeline
    post {
        // Se ejecuta si el pipeline fue exitoso
        success {
            echo 'Pipeline ejecutado exitosamente!'
        }
        // Se ejecuta si el pipeline falló en algún punto
        failure {
            echo 'El pipeline ha fallado'
        }
    }
}
