#devops #cicd 
# Creating a basic DevOps pipeline
___
- Go to `.github/workflows` in your project directory
- create a file named `ci.yml`
- It will have two `jobs`:
	- **Install and Test**
	- **Build Android**
- (Build iOS will be covered later)

___
### Install and Test
```
install-and-test:  
	runs-on: ubuntu-latest  
	steps:  
		- uses: actions/checkout@v2  
		- name: Install npm dependencies  
		  run: |  
		    npm install  
		- name: Run tests  
		  run: |  
			npm test
```

___
### Build Android
```
build-android:  
	needs: install-and-test  
	runs-on: ubuntu-latest  
		steps:  
			- uses: actions/checkout@v2  
			- name: Install npm dependencies  
		run: |  
		  npm install  
		- name: Build Android Release  
		  run: |  
			cd android && ./gradlew   
		- name: Upload Artifact  
		  uses: actions/upload-artifact@v1  
		  with:  
			name: app-release.apk  
			path: android/app/build/outputs/apk/release/
```

___
### End Result
![[Pasted image 20220828004053.png|600]]

___
### Resources
[GitHub Gist](https://gist.github.com/esxr/0131ba2cad947872a3903211a44e2e65)
[Automate React Native builds with github actions](https://medium.com/@remi.gallego/automate-react-native-builds-with-github-actions-af54212d26dc)