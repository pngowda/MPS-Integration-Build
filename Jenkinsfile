node {
	stage ('checkout'){ 
		checkout scm 
    }
	stage ('build'){
		echo "Building on branch: ${env.BRANCH_NAME}"
		if(isUnix()) {
			sh "./gradlew -b build.gradle publish"
		}
		else{
			bat "./gradlew -b build.gradle publish"
		}
	}
        
	stage ('deploy'){
		echo "Deployment stage"
		withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: '2bf4d7e9-37c7-4436-b459-b40187d8488a',
                    usernameVariable: 'Username', passwordVariable: 'Password']]) {
					bat ''' echo %Username%''' 
					bat ''' echo %Password%'''}
	}
	
}
