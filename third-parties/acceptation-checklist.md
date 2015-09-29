# Acceptation Checklist

Will contain a list of elements to check before any third party app is accepted as a delivered.

## App quality

> The app itself should have a minim acceptation quality.

* Should cover 100% of the business requirements as all wireframes provided to define that business logic related behaviour.
* All 'X' cases should be handled despite they are not defined in the designing stage, following the process of: detection - definition - design - implement - test.
* The App should be [robust]( https://en.wikipedia.org/wiki/Robustness_(computer_science) and never crash. So all errors can occur commig from external systems should be 100% handled. Some examples of Errors should be properly handled:
  * Front End App: If any of the Backends with who this app is communication with returns an error, should be properly communicated to the user.
  * Back End App: If any of the Frontends make a wrong call, the error should be communicated properly.
  * Back End App: If any of the external services returns an error, it should be properly handled.
  * Mobile App: If any of the phone services used fails or returns an error, should be properly communicated to the user and the app shouldn't fail.
* 
* Some basic stages are not acceptable and will be considered as a critic error. Some of them are:
  * Blanc stage: No answer to the client/user.
  * Not understandable error stage.
  * ...
* Shold support all platforms/devices that accomplish the 5% rule. So all browser/devices that are being used for more than 5% of the users of that app, should be supported.
* Bugs free: We consider that any accepted app be bug free.
* The delivered product should be completely bug free.
* A test suit should be delivered with the app.

## Code quality

> In C42 we build, we create and we maintain. So we care about the quality of the code, we will need to modify it, we will have in mind the developer who wrote that code.

* All new code should follow the [general C42 code guidelines](https://github.com/calendar42/developer-guide/tree/master/general-coding-style-guide).
* All modifications made in old code should have a proper comment explaining the reason of that change in ONE LINE.
* We are creating a different guidelines based on language. Take a look to the [C42 developer-guide](https://github.com/calendar42/developer-guide) and have it always in mind.
* The data used should be consistent and follow a logic structure.
* Translations should be dynamic.
* All external libraries used should be in the last version.

## Transfer process/requirements

> Tranfering information is not a simple step. It is a really imporant step where we should be sure nothing is being missing, and we will be able install, remove, modify, etc. the code we are buying

All projects should contain a README.md file in the root of the folder tree.
Template example:

* Prerequisites: All required tools/modules that this software requires to run at any enviroment with links to its page.
* Installation:
	* Troubleshooting: If there is some, a list of possible troubleshootings.
* Running
* Usage
	* API Reference
	* Examples
* Development
	* Version
	* Third party libraries
	* Code examples
	* Tests
* History
* Contributing
* Credits
* License
