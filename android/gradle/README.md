# Gradle Template Configuration files

## How to use

### Configure Gradle Library Project

- Configure your Project's `build.gradle` like this :

		buildscript {
		    repositories {
			jcenter()
		    }
		    dependencies {
			classpath 'com.android.tools.build:gradle:3.0.1'
			classpath 'com.github.dcendents:android-maven-gradle-plugin:2.0'
		    }
		}
		plugins {
		    id "com.jfrog.bintray" version "1.7.3"
		}
		allprojects {
		    repositories {
			jcenter()
		    }
		}

- In the library module's `build.gradle`, add following:

		apply plugin: 'com.android.library'

		ext {
		    bintrayRepo = 'REPOSITORY_NAME'
		    bintrayName = 'PACKAGE_NAME'

		    publishedGroupId = 'GROUP_ID'
		    libraryName = 'LIBRARY_NAME'
		    artifact = 'LIBRARY_NAME'

		    libraryDescription = 'LIBRARY_DESCRIPTION'

		    siteUrl = 'SITE_URL'
		    gitUrl = 'GIT_URL'

		    libraryVersion = 'LIBRARY_VERSION'

		    developerId = 'DEVELOPER_ID'
		    developerName = 'DEVELOPER_NAME'
		    developerEmail = 'DEVELOPER_EMAIL'
		    
		    organization = 'ORGANIZATION' // if you push to organization's repository.

		    licenseName = 'The Apache Software License, Version 2.0'
		    licenseUrl = 'http://www.apache.org/licenses/LICENSE-2.0.txt'
		    allLicenses = ["Apache-2.0"]
		}

- Finally, at the end of the library module's `build.gradle`, add:

		//These two remote files contain Bintray configuration as described above.
		apply from: 'https://raw.githubusercontent.com/KassyLab/template-files/master/android/gradle/install.gradle'
		apply from: 'https://raw.githubusercontent.com/KassyLab/template-files/master/android/gradle/bintray.gradle'

### Configure Bintray credentials

There are two methods to configure Bintray credentials :

- Add the two environment variables following :

		export BINTRAY_USER="Your Bintray user ID"
		export BINTRAY_KEY="Your Bintray API Key"

- Run Bintray upload command with following arguments :

		./gradlew build bintrayUpload -PbintrayUser=<Your Bintray user ID> -PbintrayApiKey=<Your Bintray API Key>

### Uploading to Bintray

CD to Root of Android Studio Project, and run these commands:

	./gradlew install
	./gradlew build bintrayUpload

## License

	Copyright © 2016 KassyLab

	Licensed under the Apache License, Version 2.0 (the "License");
	you may not use this file except in compliance with the License.
	You may obtain a copy of the License at

	http://www.apache.org/licenses/LICENSE-2.0

	Unless required by applicable law or agreed to in writing, software
	distributed under the License is distributed on an "AS IS" BASIS,
	WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or 
	implied.
	See the License for the specific language governing permissions and
	limitations under the License.
