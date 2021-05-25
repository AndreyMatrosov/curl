node('docker') {
    stage('Checkout') {
        cleanWS()
        checkout([$class: 'GitSCM',
                  branches: [[name: '*/master']],
                  extensions: [],
                  userRemoteConfigs: [[credentialsId: 'jenkins_ssh',
                  url: 'https://github.com/AndreyMatrosov/curl']]])       
    }
    stage('Build') {
        cmakeBuild(buildDir: 'build',
                   buildType: 'Release',
                   installation: 'CMake',
                   sourceDir: 'https://github.com/AndreyMatrosov/curl')
    }
}
