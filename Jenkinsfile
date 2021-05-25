node {
    stage('Checkout') {
        cleanWs()
        checkout([$class: 'GitSCM',
                  branches: [[name: '*/master']],
                  extensions: [],
                  userRemoteConfigs: [[credentialsId: 'jenkins_ssh',
                  url: 'https://github.com/AndreyMatrosov/curl']]])       
    }
    stage('Build') {
        cmakeBuild(buildDir: 'build',
                   generator: 'Unix Makefiles',
                   buildType: 'Release',
                   installation: 'CMake',
                   sourceDir: 'CMakeLists.txt')
    }
    stage('Deploy') {
        sh 'echo "ok"'
    }
}
