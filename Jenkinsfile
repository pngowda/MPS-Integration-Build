node('master') {
	def buildFile1     = './MPS_Version_Snapshot_local.gradle'
	def buildFile2     = './MPS_Project_Rebase_local.gradle'
	def buildWrapper  = './gradlew'
	
		stage ('checkout'){ 
			checkout scm
		}
		stage ('build'){
			echo "Building on branch: ${env.BRANCH_NAME}"
			if(isUnix()) {
				sh "chmod +x ${buildWrapper}"
				sh "${buildWrapper} -b ${buildFile1} publish"
			}
			else{
				bat "${buildWrapper} -b ${buildFile1} publish"
			}
		}

		stage ('test'){
			 echo "Running tests on branch: ${env.BRANCH_NAME}"
		try {
			 if(isUnix()) {
				sh "chmod +x ${buildWrapper}"
				sh "${buildWrapper} -b ${buildFile2} cloneGitRepo"
			}
			else{
				bat "${buildWrapper} -b ${buildFile2} cloneGitRepo"
			}
			
		}
		catch(err) {
				echo "### There were test failures:\n${err}"
			}
		}
	
}

