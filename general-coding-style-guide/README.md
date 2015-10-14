





C42 General Coding Guide
========================

*How to make your code readers and users purr ...*


These are the guidelines that apply to any computer language. Note that there are no rules without exceptions, but these exception should be explained.


Quotes
------

Some random quotes:
* Software is a great combination of artistry and engineering (Bill Gates),
* Always code as if the guy who ends up maintaining your code will be a violent psychopath who knows where you live (Martin Golding),
* When debugging, novices insert corrective code; experts remove defective code (Richard Pattis),
* One of my most productive days was throwing away 1000 lines of code (Ken Thompson),
* Programming is like sex. One mistake and you have to support it for the rest of your life (Michael Sinz),
* Beauty of style and harmony and grace and good rhythm depends on simplicity. (Plato),
* Code is more often read (and hopefully used) than it is written (Guido van Rossum).


Basics
------

Some rules apply to all languages, although more strictly to some.

0. Think before starting to code; walk outside, think again; ask yourself: 
	* why am i building this?
	* what will it be used for?
	* who will use it?
	* what do they need?
	* where should it be placed?
	* how will it be named?
	* what is situation specific and what can be reused? 
0. Code should be modelled after the (perception of) reality of the user (problem domain, business domain). This hould be done at an early stage and should represent the logic and structure of this reality as closely as possible,
0. Code should be modular and decoupled; different aspects of coding (business logic, logging, error handling, inter process communication, etc) should be separated as much as possible, 
0. Names should be clear and preferably short; if names need to be long to be clear, most likely the code should be moved to a more logical place,
0. Functions should be short and have a clear single purpose; this improves readability, reusability, testability and reduces the need for extensive commentary,
0. Information should be stored in one and only one place (except for very specific purposes like caching), otherwise the information has to be kept in sync continuously to prevent invalid program states,
0. Variables, functions, constants, attributes and the like should not be reused unless they have the same exact logical meaning, otherwise,  refactoring (when the differences become apparent) will be complicated and error prone,
0. Comments should explain the why of the code, not the what; the code itself is the what of the code.

Decoupling we will discuss in this chapter, because it may be the main objective to be able to maintain complex software system in the long run in any language. 


Decoupling
----------

To be able to handle increasingly large code bases, the main principles to be used is decoupling. Decoupling means separating different functionality in code modules with a specific purpose. The language often determines the possibilities for decoupling (e.g. is it object oriented?).

Note that as soon as a specific set of functions can be though of as a whole, it is a candidate for decoupling and at least an attempt should be made to do so. Any function and set of functions that can be moved into a separate function, class, module or other structure, will be more reusable and will reduce the complexity of the code it is removed from.

This is a list of items that should be decoupled (as far as possible):

* Interface (api) and implementation: interfaces should always be defined in clear methods (with clear names) and be usable without much knowledge of the implementation. Clear function names, intuitive results sets and simple documentation are important. The complexities of implementation should (as far as possible) not percolate through the interface. Someone creating a user interface should not have to know how antialiasing is implemented to be able to turn it on, 
* Error handling: This is usually achieved by using exceptions for error handling. In some languages (e.g. python) error handlling might be further decoupled by using decorators. Exception handling creates the possibility to follow a separate code path for errors without clogging up other code,
* Logging: Logging can be used for many purposes (debugging, statistics, optimization, etc.). It not add functionality to the other code, it just reports on it's execution. Sometimes it is necessary to adding logging lines in normal functions, these should be sinfgle lines. In some languages logging can be further decoupled by using e.g. decorators and other techniques,
* Data validation: Thi sis essential to protect system state from incorrect external data (external can be relative). Decoupling can be achieved by different techniques, but should be at least in separate methods, and preferably be centrally managed, to be able to determine its completeness. Data structures should protect the integrity of their structure, preferably on instantiation, possibly in constructors but other decoupling techniques are possible (like descriptors in python, constraints in databases),
* Authentication and authorization, to have and keep a clear view on who is who and who can do what on a system, A&A needs to be decoupled and be added to the program flow in specific, easy to control places (early in the flow),
* MVC or Model, View, Controller: this splits "normal" functionality in three parts, where the user uses the Controller, which manipulates the Model (data), which updates the View (user interface), which allows the user to use the controller again ..
* Business Logic and Infrastructure (on a code level): here the business logic handles the actual user reality e.g. in terms of vehicle routes, customer account, gameplay, etc. Infrastructure is concerned with e.g. interprocess communication, logging, technical validation, authentication and authorization. 

Business logic (normal functionality) should be decoupled as well. It is essential for large systems to model the data and functionality thoroughly before any coding takes place. Ofcourse it is often impossible to predict all functionality a system will support, delaying untill at least current current  model is clear, combined with decoupling described above, keep the systems manageable without major overhauls for a much longer time.

Exact techiques of decoupleing will be detailed in the language specific guide lines.


System Maintenance
------------------

0. Non business related code: The code shouldn't contain any customer name, entity or label that is related with the customer or the business case that is being build. So var names like: expertName, isExpertUser are wrong.
0. Tool related code: The words used to name the different vars/methods/objects/files should be related to the tool we are creating. So names like: userName, isUserType are correct.
0. To allow to create an autogenerated documentation, comments should be written following some of our auto-generate documentation tools. For front end applications we use [yuiDocs](http://yui.github.io/yuidoc/ "yuiDocs	").
0. Translations should be dynamic. We have multiple ways to provide of multilingual labels, texts, etc. Mainly using our rest API where we can set an object containg all texts related to an app. For that reason, the way as that texts are being rendered in the templates should be totally dinamic.
0. All libraries and plugins used in the app should be in the last version.
0. The eventual logic should be easy to document and easy to understand for anyone
