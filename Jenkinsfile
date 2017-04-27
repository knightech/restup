node {
    stage "Checkout"
    git url: "https://github.com/knightech/restup.git"
    
    stage "Build/Analyse/Test"
    sh "./gradlew clean build"
    archiveUnitTestResults()
    
    stage "Generate AMI"
    sh "./gradlew build buildDocker"
}

def archiveUnitTestResults() {
    step([$class: "JUnitResultArchiver", testResults: "build/**/TEST-*.xml"])
}
