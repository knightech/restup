node {
    stage "Checkout"
    git url: "https://github.com/knightech/restup.git"
    
    stage "Build/Analyse/Test"
    sh "./gradlew clean build"
    archiveUnitTestResults()
    archiveCheckstyleResults()
    
    stage "Generate AMI"
    sh "./gradlew buildDocker"
}

def archiveUnitTestResults() {
    step([$class: "JUnitResultArchiver", testResults: "build/**/TEST-*.xml"])
}

def archiveCheckstyleResults() {
    step([$class: "CheckStylePublisher",
          canComputeNew: false,
          defaultEncoding: "",
          healthy: "",
          pattern: "build/reports/checkstyle/main.xml",
          unHealthy: ""])
}
