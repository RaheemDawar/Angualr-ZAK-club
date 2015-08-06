# AngularJS

**AngularJS** is the JavaScript MVC with awesome features to build rich client side MVC. It acts as a glue between HTML and JavaScript objects, i.e any update on your view will immediately effect without any DOM manipulation or event bindings.

#### Components:

- **The Model :**
The model is responsible for managing application data. It responds to the request from view and to the instructions from controller to update itself.

- **The View :**
Presenting data in particular format based on the controller’s decision to present the data.

- **The Controller :**
Based on the input, Controller performs interactions with data model objects. Controller receives input, validates it and then performs business operations that modifies the state of the model.

#### AngularJS directives:

- **ng-app :** Initializes the application when web page containing Angular JS Application is loaded.

- **ng-init :** stores the values to the variables used in the application.

- **ng-model :** defines model/variable to be used in the application.

- **ng-repeat :** repeat Html elements in the collections.

#### Features of AnuglarJS:

- **Data-binding :** It is the automatic synchronization of data between model and view components.
- **Scope :**These are objects that refer to the model. They act as a glue between controller and view.
- **Controller:**These are Javascript functions that are bound to a particular scope.
- **Services:** AngularJS come with several built-in services for example $http to make a XMLHttpRequests. These are singleton objects which are instantiated only once in app.

- **Filters:** These select a subset of items from an array and returns a new array.
- **Directives:** Directives are markers on DOM elements (such as elements, attributes, css, and more). These can be used to create custom HTML tags that serve as new, custom widgets. AngularJS has built-in directives (ngBind, ngModel...)
- **Templates:** These are the rendered view with information from the controller and model. These can be a single file (like index.html) or multiple views in one page using "partials".
- **Routing:** It is concept of switching views.
- **Deep Linking:** Deep linking allows you to encode the state of application in the URL so that it can be bookmarked. The application can then be restored from the URL to the same state.
- **Dependency Injection:** AngularJS has a built-in dependency injection subsystem that helps the developer by making the application easier to develop, understand, and test.

#### Few Disadvantages of AngularJS to discuss:
0. Security issue : It’s recommended to keep server side authentication as angular is like javascript only framework.
1. considering usecase like user disabling javascript on the page, then only the basic page will be shown. I don’t think that particular use case need to be considered.


#### Please go through the basic example of AngularJS:

```html

<html>
<head>
<title>Angular JS Example</title>
<script src="http://ajax.googleapis.com/ajax/libs/angularjs/1.3.14/angular.min.js"></script>
</head>
<body>
<h2>AngularJS Sample Application</h2>
<div ng-app="mainApp" ng-controller="studentController">

Enter first name: <input type="text" ng-model="student.firstName"><br><br>
Enter last name: <input type="text" ng-model="student.lastName"><br>
<br>
You are entering: {{student.fullName()}}
</div>
<script>
var mainApp = angular.module("mainApp", []);

mainApp.controller('studentController', function($scope) {
   $scope.student = {
      firstName: "zakir",
      lastName: "akihtrak",
      fullName: function() {
         var studentObject;
         studentObject = $scope.student;
         return studentObject.firstName + " " + studentObject.lastName;
      }
   };
});
</script>
</body>
</html>

```

The above code looks like this
![Sample AngularJS image] (https://github.com/Zakir289/Angualr-car-race/blob/master/AngluarSample.png)



AngularJS provide services like `$http, $route, $window, $location etc`. Each service has specific defintion for example,  $http is used to make ajax call to get the server data. $route is used to define the routing information and so on. Inbuild services are always prefixed with $ symbol. Controllers, filters can call them as on requirement basis. Services are normally injected using dependency injection mechanism of AngularJS.



# Zak's club implementation

Here goes a funny example for AngularJS by using some template which i found on web. I am going to develop a Happy club application where a group of friends try to help others and make the society Happy. 

#### Steps to run the application
- Install any webserver on your machine, I had used Apache Tomcat. 
- Download the code and place it in webapps folder of Tocat.
- Now start the server, and reach the index.html page.
- And the magic starts.......

The basic areas of the Page include
- Home
- Facilities
- Pricing
- About
- FAQ
- Contact

I am using Bootstrap as it fits awesome for these kind of funny sites. Angular JS is more suitable for Single Page application, here I did not included any back end code rather just wrote it as front end stuff.


All the necessery libraries are included in `index.html` instead of rewriting the code.
```html
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css">
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap-theme.min.css">
    <link href="http://maxcdn.bootstrapcdn.com/font-awesome/4.1.0/css/font-awesome.min.css" rel="stylesheet">


<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.2.18/angular.min.js"></script>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.2.18/angular-route.min.js"></script>

<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.0/jquery.min.js"></script>
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.2.0/js/bootstrap.min.js"></script>

```
### Angular Architecture

##### 1.Angular Directives

 **ng-app** directive binds the Angular app to this single page’s html body.
 **ng-include** loads the necessery files on the page.
 **ng-view** provides a container in which Angular routes include the pages
```html


<body ng-app="AngularTutorial">

<div ng-include='"templates/header.html"'></div>
<div ng-view></div>
<div ng-include='"templates/footer.html"'></div>
```

##### 2.Templates
Instead of writing Navigation code(Header), Fotter for each and every page, we write header and fotter here and include them in index.html as we do  in most of the MVC frameworks.

##### 3.Angular Routes

Angular routes provide helps to load other html pages. 

  $routeProvider
    // Home
    .when("/", {templateUrl: "partials/home.html", controller: "PageCtrl"})
    // Pages
    .when("/about", {templateUrl: "partials/about.html", controller: "PageCtrl"})
    .when("/faq", {templateUrl: "partials/faq.html", controller: "PageCtrl"})
    .when("/pricing", {templateUrl: "partials/pricing.html", controller: "PageCtrl"})
    .when("/services", {templateUrl: "partials/services.html", controller: "PageCtrl"})
    .when("/contact", {templateUrl: "partials/contact.html", controller: "PageCtrl"})

    
    The final page looks relly awesome. The output will be ten times more than the work done by us.
    
    
## Here is how the site looks finally

### 1.Entire Home page
Its the complete glance of the home page. The below image is the complete home page

![Home] (https://github.com/Zakir289/Angualr-ZAK-club/blob/master/DocumentedImages/Home_page.png)

### 2. Visible Home page
This is visible area of the home page in Macbook 11 inches	

![Home] (https://github.com/Zakir289/Angualr-ZAK-club/blob/master/DocumentedImages/Home1.png)
### 3.Contact page
This page describes how can people reach out ZAK's club through onlne
![Contact] (https://github.com/Zakir289/Angualr-ZAK-club/blob/master/DocumentedImages/Contact.png)
### 4.FAQ page
![FAQ] (https://github.com/Zakir289/Angualr-ZAK-club/blob/master/DocumentedImages/FAQ.png)
#### 5.Facilities
Facilities page provides the information about the services
![Facilities](https://github.com/Zakir289/Angualr-ZAK-club/blob/master/DocumentedImages/Facilities.png)
#### 6.About
About page include information about how the club is formed and team info
![About](https://github.com/Zakir289/Angualr-ZAK-club/blob/master/DocumentedImages/About.png)
#### This how it is visible on Macbook 11 inches
![About](https://github.com/Zakir289/Angualr-ZAK-club/blob/master/DocumentedImages/About1.png)
#### The most funniest of all:)
![pricing](https://github.com/Zakir289/Angualr-ZAK-club/blob/master/DocumentedImages/pricing.png)

The above application did not used much of Angular features will upate it with few other stuff
