node('master') {
	def buildFile     = './MPS_Version_Snapshot.gradle'
	def buildWrapper  = './gradlew'
	
		stage ('checkout'){ 
			checkout scm
		}
		stage ('build'){
			echo "Building on branch: ${env.BRANCH_NAME}"
			if(isUnix()) {
				sh "chmod +x ${buildWrapper}"
				sh "${buildWrapper} -b ${buildFile} publish"
			}
			else{
				bat "${buildWrapper} -b ${buildFile} publish"
			}
		}

		stage ('test'){
			 echo "Running tests on branch: ${env.BRANCH_NAME}"
		try {
			 if(isUnix()) {
				sh "chmod +x ${buildWrapper}"
				sh "${buildWrapper} -b ${buildFile} publish"
			}
			else{
				bat "${buildWrapper} -b ${buildFile} publish"
			}
			
		}
		catch(err) {
				echo "### There were test failures:\n${err}"
			}
		}
	
}

