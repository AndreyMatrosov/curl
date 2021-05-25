node {
    stage('Checkout') {
        if  (env.BRANCH_NAME == ' master ' ) {
            cleanWs()
            checkout([$class: 'GitSCM',
                    branches: [[name: '*/master']],
                    extensions: [],
                    userRemoteConfigs: [[credentialsId: 'jenkins_ssh',
                    url: 'https://github.com/AndreyMatrosov/curl']]])
        } else {
            echo 'not master branch'   
        }
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
