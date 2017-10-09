def gradleOpts ='--no-daemon --info --stacktrace'
node {
	stage'checkout'    
		checkout scm 
    
	stage('build')
		echo "Building on branch: ${env.BRANCH_NAME}"
		//sh "./gradlew ${gradleOpts} -b build.gradle publish"
        
	stage'deploy'    
		echo "Deployment stage"
}
