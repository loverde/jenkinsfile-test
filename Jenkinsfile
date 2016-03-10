#!groovy


stage name: 'setup'
node {
    if (isUnix()) {
        echo "unix mode"
	    sh 'pwd'
        sh "ls -la"
    } else {
        echo "windows mode"
        bat "pwd"
        bat "dir"
    }
/*
    wrap([$class: 'Groovy']) {
        def script = '''
        println "\n\nSystem Properties"
        System.properties.each { k,v -> println "$k = $v" }

        println "\n\nEnvironment"
        System.getenv().each { k,v -> println "$k = $v" }
'''
    }
*/

    // Testing
    git url: 'https://github.com/loverde/jenkinsfile-test'
}

stage name: 'build'
node {
    isUnix() ?  sh './gradlew clean build' : bat './gradlew.bat clean build'
}

stage name: 'postbuild'
node {
    isUnix() ?  sh 'ls -la' : bat 'dir'
}
