stage('Preparar carpeta app') {
    steps {
        sh '''
            echo "📁 Contenido antes de copiar:"
            ls -la

            echo "📂 Creando carpeta app/"
            mkdir -p app

            echo "📄 Copiando archivos al interior de app/"
            cp -v package.json package-lock.json app/ || true
            cp -vr src app/
            cp -vr tests app/

            echo "📁 Contenido dentro de app/:"
            ls -la app
        '''
    }
}
