node {
	def buildFile     = './code/test/build.gradle'
	def buildWrapper  = './code/test/gradlew'
	
    stage ('checkout'){ 
        checkout scm
    }
    stage ('build'){
        echo "Building on branch: ${env.BRANCH_NAME}"
        if(isUnix()) {
            sh "buildWrapper -b buildFile buildrun"
        }
        else{
            bat "buildWrapper -b buildFile buildrun"
        }
    }

    stage ('test'){
         echo "Running tests on branch: ${env.BRANCH_NAME}"
		try {
			if(isUnix()) {
				sh "buildWrapper -b buildFile testrun
			}
			else{
				bat "buildWrapper -b buildFile testrun"
			}
			step([$class: 'JUnitResultArchiver', testResults: '*/TEST-*.xml'])
		}
		catch(err) {
			echo "### There were test failures:\n${err}"
		}
	}
}