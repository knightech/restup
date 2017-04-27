echo "workflow"

stage 'build'
node {

    echo "checkout from GitHub"
    git 'https://github.com/knightech/restup.git'

    echo "build with wrapper"
    sh './gradlew build -x test'

    archive 'build/libs/*.jar'

}

stage 'test'
node {
    sh './gradlew clean test'

}