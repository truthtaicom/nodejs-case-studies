##Build a Simple REST Application with AngularJS Node API with Strongloop##

1.First you need to install the StrongLoop API server which is an NPM command.
```
$ npm install -g strongloop
```
2.You will enter in the directory where you want to create the project and your project name, which in this case will be example-api.
```
$ slc loopback
```
3.Now that the project is generated, we will jump into the project directory.
```
$ cd example-api
```
4.We then set up our datasource and point it to an ItemsDB database. This is where we choose MongoDB as our datasource.
```
$ slc loopback:datasource MongoDB
```
5.And now to define our model. This is where we choose the datasource, input the plural form of the model name, and define the properties of the model.
```
$ slc loopback:model Member
```
6.Because we are using MongoDB, we need to install the loopback-connector-mongodb package.
```
$ npm install loopback-connector-mongodb
```
7.Make dir client/dist/js/
```
mkdir client/dist/js/
```
8.Generated Loopback Angular SDK Service
```
lb-ng -m ExampleAPI -u http://localhost:3000/api server/server.js client/dist/js/lb-services.js
```
>-m, --module-name [name]   The name for generated Angular module.  Default is "lbServices".
>-u, --url [url] URL of the REST API endpoint.
>lb-ng [ options]  path-to-server-script [ path-to-generated-services]

9.And we are ready to roll!
```
$ slc run
```
> You will then be able to go to http://localhost:3000/explorer to see the StrongLoop API Explorer; this is a great utility for exploring and interacting with your new API.

## Follow these steps to use the generated services inside your AngularJS application:
1.Install packages ith NPM install && bower install
```
bower init ( if not exits)
```
```
bower install --save angular angular-animate angular-bootstrap angular-ladda angular-resource angular-ui-router angular-ui-notification bootstrap font-awesome jquery angular-messages
```
```
npm install -g gulp ( if dont install Gulp with global)
```
```
npm install gulp gulp-uglify gulp-concat gulp-minify-css gulp-sourcemaps gulp-rename gulp-nodemon gulp-loopback-sdk-angular gulp-jshint
```
2.Include **js/lb-services.js** in your **index.html** file
```
<script src="js/lb-services.js"></script>
```
>You'll need to set up static middleware to serve the client script. See Defining middleware for more information.
Register the AngularJS module  lbServices  as a dependency of your app.  Add 'lbServices' to the angular.module() call in  the main JavaScript file of your Angular (client) app, as follows:

```
angular.module('my-app-module',
  ['ngRoute' /* etc */, 'lbServices', 'my-app.controllers'])
To call a method on a model from your controller, add the model name as a dependency of the controller; for example:
 // access User model
module.controller('LoginCtrl', function($scope, Member, $location, $state, Notification) {
  $scope.login = function() {
    $scope.loginResult = User.login($scope.credentials,
      function() {
        // success
      }, function(res) {
        // error
      });
```      
3.Client configuration

>You can configure some aspects of the generated services within the AngularJS client application using the LoopBackResourceProvider object, as illustrated below. This object is available to configuration blocks only; for more information, see  Module Loading & Dependencies  in the AngularJS documentation.
app.js

```
angular.module('my-app-module')
  .config(function(LoopBackResourceProvider) {

    // Use a custom auth header instead of the default 'Authorization'
    LoopBackResourceProvider.setAuthHeader('X-Access-Token');

    // Change the URL where to access the LoopBack REST API server
    LoopBackResourceProvider.setUrlBase('http://api.example.com/');
  });
```  

See example code
>[index.html](https://github.com/truthtai/e-commerce-case-studies/blob/master/Day%2010/index.html)
>[app.js](https://github.com/truthtai/e-commerce-case-studies/blob/master/Day%2010/app.js)
>[gulpfile.js](https://github.com/truthtai/e-commerce-case-studies/blob/master/Day%2010/gulpfile.js)

See [LoopBackResourceProvider](http://apidocs.strongloop.com/loopback-sdk-angular/#loopbackresourceprovider) API docs for the list of all available options.

See [AngularJS JavaScript SDK](https://docs.strongloop.com/display/public/LB/AngularJS+JavaScript+SDK)
