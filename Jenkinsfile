node ('master') {
    stage('Checkout') {
           cleanWs()
           checkout([$class: 'GitSCM',
                   branches: [[name: '*/master']],
                   extensions: [],
                   userRemoteConfigs: [[credentialsId: 'jenkins_ssh',
                   url: 'https://github.com/AndreyMatrosov/curl']]])
    }
    withEnv(['CMAKE_C_COMPILER=ninja',
             'CMAKE_MAKE_PROGRAM=/usr/bin/ninja']) {
        stage('Build') {
            cmakeBuild(buildDir: 'build',
                   generator: 'Ninja',
                   buildType: 'Release',
                   installation: 'CMake',
                   sourceDir: 'CMakeLists.txt')
        }
    }
    stage('Test') {
        ctest installation: 'CMake', workingDir: 'tests/unit'
    }
}
