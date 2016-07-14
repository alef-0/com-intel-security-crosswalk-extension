App Security API
================ 
The App Security API enables the use of security properties and capabilities on the platform, using a new set of API defined for application developers.
You are not required to be a security expert to make good use of the API. Key elements, such as encryption of data and establishments of capabilities, is abstracted and done by the API implementation, for you.
For example
-	Use the API to store (E.g. cache) data locally, using the device non-volatile storage. Data protection/encryption will be done for you by the API implementation 
-	Establish a connection with remote server (E.g. XHR) using a protected channel. SSL/TLS establishment and usage will be done for you by the API implementation

For more information please visit our API documentation @ https://software.intel.com/en-us/app-security-api/api
Additionally please see our demo applications:
	- "MyPrivateNotes":		https://software.intel.com/en-us/xdk/article/my-private-notes-sample
	- "MyPrivatePhotos":	https://software.intel.com/en-us/xdk/article/my-private-photos-sample		

		
Crosswalk extension
===================
	
	The project contains 'src' folder which contains the App Security API extension (the executable file) and 'www' folder which contains the javascript API.
		
	How to use the extension
	========================
		Include appSecurityApi.js and q.js files www directory in your web application. 
		Then, create a folder within your root directory of the web app 'AppSecurityAPI' (or any other name, but keep in mind to set the same value in step 1.a) and copy the entire content of 'src' folder into it.
		
		For creating the MSI please:		
			a. Add the extension to the manifest file by editing the value of key 'xwalk_extensions' in manifest file: {'xwalk_extensions':'AppSecurityAPI'}. More details in https://github.com/crosswalk-project/crosswalk-app-tools/blob/master/manifest.md)
			b. Create a MSI installer by openning command line and executing 'crosswalk-pkg -p windows <path>' details in https://github.com/crosswalk-project/crosswalk-app-tools

	Redistributable
	===============
	
	You have to install Visual C++ Redistributable for Visual Studio 2015 on the system before you call the dll. 
	When you deploy your application, make sure that Visual C++ Redistributable for Visual Studio 2015 is installed before you run the application.
	
	Known Issues (Crosswalk extension only)
	============
	1. The extension creates files in the user's AppData (example: C:\Users\MyUser\AppData\Local\TestApp_xsapi), the application should remove the items during uninstall operation.

Hardware Root Of Trust
======================
The software stack can utilize Intel(R) platform security technologies, under the hood, with no need to change the API at the application level.
This enhancement is supported on Intel(R) platforms that have Intel(R) Active Management Technology hardware enabled and 
 also have the supporting software stack on the platform.
For more information on the security technologies, please refer to https://software.intel.com/en-us/amt-sdk

Cordova plugin 
==============
For Cordova plugin please see https://github.com/AppSecurityApi/com-intel-security-cordova-plugin.git