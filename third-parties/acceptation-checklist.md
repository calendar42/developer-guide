# Acceptation Checklist (WIP)

Will contain a list of elements to check before any third party app is accepted as a delivered.

> The key words **"MUST"**, **"MUST NOT"**, **"REQUIRED"**, **"SHALL"**, **"SHALL NOT"**, **"SHOULD"**, **"SHOULD NOT"**, **"RECOMMENDED"**, **"MAY"**, and **"OPTIONAL"** in this document are to be interpreted as described in [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt).

## App quality

### Business requirements

> In C42 we build code to construct a new and better reality. There is no code without a goal.

* The main goal of the app must be accomplished and any error or bug found needs to be fixed. This can be modified based on contract or in collaboration process.
* We consider the following errors/bugs classification:
   *  Show stoppers: Those errors that doesn't allow to the user to accomplish on of the main goals of the app.
   * Critical: A sub-goal of the app can't be reached because this error.
   * Major: Error that annoy most part of the users of the app.
   * Minor: Other minor bugs like copy errors and small style errors. For example.

### UX quality

> All apps with a front end side must accomplish the C42 quality that we are always trying to bring to our users.

* Must cover 100% of the requirements as all wireframes provided.
* Performance. The user experience should not be affected for the slow response of the app.

### Basic App quality

> The app itself must have a minimum acceptation quality.

* All edge cases must be handled even if they are not defined in the designing stage, following the process of: detection - definition - design - implement - test.
* The App must be [robust]( https://en.wikipedia.org/wiki/Robustness_(computer_science) and never crash. So all errors that can occur coming from external systems must be 100% handled. Some examples of Errors must be properly handled:
  * Front End App
      * If any of the Backends used returns an error, must be properly communicated to the user.
      * If any of the Backends used changes the return of a call, the front end app must not crash and communicate a proper error message to the user.
  * Back End App
      * If any of the front end apps makes a wrong call, the error must be communicated properly.
      * If any of the external services returns an error, it must be properly handled.
  * Mobile App
      * If any of the device services fails or returns an error, must be properly communicated to the user and the app shouldn't crash.
* Some basic stages are not acceptable and will be considered as a critic error. Some of them are:
  * Blanc stage: No answer to the client/user.
  * Not understandable or user friendly error stage.
  * ...
* Must support all platforms/devices that accomplish the 5% rule. So all browser/devices that are being used for more than 5% of the users of that app, must be supported.
* Bugs free: We consider that any accepted app be bug free.
* The delivered product must be completely bug free.
* A test suit should be delivered with the app.

## Code quality

> In C42 we build, we create and we maintain. So we care about the quality of the code, we will need to modify it, we will have in mind the developer who wrote that code.

* All new code should follow the [general C42 code guidelines](https://github.com/calendar42/developer-guide/tree/master/general-coding-style-guide).
* We are creating a different guidelines based on language. Take a look to the [C42 developer-guide](https://github.com/calendar42/developer-guide) and have it always in mind.
* All modifications made in old code should have a proper comment explaining the reason of that change in ONE LINE.
* The data used should be consistent and follow a logic structure.
* Translations should be dynamic.
* All external libraries used should be in the last version.

## Transfer process/requirements

> Transferring information is not a simple step. It is a really important step where we must be sure nothing is missing, and we will be able install, remove, modify, etc. the code we are buying.

All projects should contain a README.md file in the root of the folder tree.
Structure example:

* Prerequisites: All required tools/modules that this software requires to run at any environment with links to its page.
* Installation:
	* Troubleshooting: If there is some, a list of possible trouble-shootings.
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
