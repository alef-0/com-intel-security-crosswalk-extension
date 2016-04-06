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
	
	You can find the extension dll file (IntelSecurityServicesExtension.dll) and the JavaScript file (appSecurityApi_XW.js) in windows_crosswalk directory
	
	How to use the extension
	========================
		Include the appSecurityApi_XW.js file from windows_crosswalk directory into your application, you have two modes to work with the dll:
		
		Crosswalk Shared Mode 
		=====================
		1. From the folder includes index.html
			python -m http.server 8000
		2. From Crosswalk executable folder - 'PathToDLL' appears in the command line below denotes the location where Crosswalk extension 'IntelSecurityServicesExtension.dll' is placed
			xwalk.exe --allow-external-extensions-for-remote-sources --external-extensions-path=PathToDLL http://localhost:8000
		3. See more details in https://crosswalk-project.org/documentation/windows/extensions.html 
	
		MSI Installer
		=============
		Add the extension to the manifest file (in manifest file: 'xwalk_extensions':'IntelSecurityServicesExtension.dll' 
			details in https://github.com/crosswalk-project/crosswalk-app-tools/blob/master/manifest.md)
		Create a MSI installer: crosswalk-pkg -p windows <path> 
			details in https://github.com/crosswalk-project/crosswalk-app-tools
			
	
	Redistributable
	===============
	
	You have to install Visual C++ Redistributable for Visual Studio 2015 on the system before you call the dll. 
	When you deploy your application, make sure that Visual C++ Redistributable for Visual Studio 2015 is installed before you run the application.
	
	Known Issues (Crosswalk extension only)
	============
	1. API calls are synchronous (no support for parallel execution in the current version). 
	2. The extension creates files in the user's AppData (example: C:\Users\MyUser\AppData\Local\TestApp_xsapi), the application should remove the items during uninstall operation.

Cordova plugin 
==============
	For Cordova plugin please see https://github.com/AppSecurityApi/com-intel-security-cordova-plugin.git