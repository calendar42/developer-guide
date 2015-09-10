# Acceptation Checklist

Will contain a list of elements to check before any third party app is accepted as a delivered.

## App quality

> The app itself should have a minim acceptation quality.

* Should cover 100% of the business requirements as all wireframes provided to define that business logic related behaviour.
* No blanc or empty states: Shouldn't exist any change that the app stays in a 'no-state' state. A blanc page, without any feedback is a really bad state.
* Shold support all browsers/devices that accomplish the 5% rule. So all browser/devices that are being used for more than 5% of the users of that app, should be supported.
* Bugs free: We consider that any accepted app be bug free.
* Errors: The app should cover absolutelly all possible error states and never crash.

## Code quality

> In C42 we build, we create and we maintain. So we care about the quality of the code, we will need to modify it, we will have in mind the developer who wrote that code.

* We created a simple [code style guideline](https://github.com/calendar42/developer-guide/tree/master/general-coding-style-guide) where we can find what we understand as a code quality.

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