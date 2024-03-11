# practical

Practical-01 
Title: -Create schema for Blog Post using MongoDB data models 
Programs: 
1. Embedded Data Model 
{ 
_id: 
postid:   , title:   , url:   , category:  , likes:   , 
author_details: {  
	firstName: 	 	, 
 	 	 	lastNme: 	 	 	,  	 	 	DOB:  	 	  	 	}, 
author_contact: {  
phone:  	,  	 	 	email:  	  	 	}, 
author_address: {  
	city: 	 	, 
 	 	 	state:  	 	,  	 	 	country: 	 	 	 
	 	 	}, 
comments: {  
	post_by: 	 	, 
 	 	 	comment: 	 	 	,  	 	 	dateTime: 	 	 	 	,  	 	 	likes:  	 	 	 
	 	 	 	}, 
} 
 
2. Normalized Data Model 
Post 
{ 
_id:<object100> 
postid:  	 	, title: 	 	 	, url: 	 	 	, category: 	 	, likes:  
SYBSc(CS) 	PRACTICAL-1 	AAD 
} 
 
author_details 
{  
postDocId:<object100>, 
	firstName: 	 	, 
lastNme: 	 	 	, DOB:  	 	 
} 
 
author_contact 
{  
postDocId:<object100>, 
phone:  	, email:  	 
} 
 
author_address 
{ 
postDocId:<object100>, 
city: 	 	, state:  	 	, country: 	 	 	 
} 
 
Comments 
{  
postDocId:<object100>, post_by: 	 	, comment: 	 	 	, dateTime: 	 	 	 	, likes:  	 	 	 
} 
 
Conclusion: 



Practical-02 
Title: - Write a program to implement CRUD operations on MongoDB. 
Programs: 	 
1.	Create Database: use     post 
  
 
2.	Create Collection: db.createCollection("post") 
  
 
3.	Insert document using insertOne( ) db.post.insertOne({   title: "AAD",   body: "MongoDB",   category: "Software", 
  likes: 10,   date: Date() 
}) 
  
 
4.	Insert document using insertMany( ) db.post.insertMany([ 
{   title: "Android",   body: "Flutter",   category: "Software", 
  likes: 20,   date: Date() 
}, {   title: "Computer Network",   body: "Cisco Packet Tracer",   category: "Networking", 
  likes: 14, 
  date: Date() 
}, {   title: "Microprocessor",   body: "Instruction Set",   category: "Hardware", 
  likes: 16,   date: Date() 
}, {   title: "MEAN Stack",   body: "Angular JS",   category: "Software", 
  likes: 33,   date: Date() 
} 
]) 
  
 
5.	find( ) and findOne( ) db.post.find() 
  
 
db.post.find({category: "Software"}) 
  
 
db.post.findOne({category: "Software"}) 
  
 
db.post.find({}, {title: 1, date: 1}) 
  
 
6.	updateOne( ) and updateMany( ) 
db.post.updateOne( { title: "Microprocessor" }, { $set: { likes: 40 } } ) db.post.find({ title: "Microprocessor" }) 
  
 
db.post.updateOne(  
  { title: "Android" },  
  { 
    $set:  
      { 
        title: "Cloud Computing",         body: "SAAS",         category: "Software", 
        likes: 12,         date: Date() 
      } 
  },  
  { upsert: true } 
) 
db.post.find({title: "Cloud Computing"}) 

db.post.updateMany({}, { $inc: { likes: 10 } }) db.post.find() 
  
 
7. deleteOne( ) and deleteMany( ) db.post.deleteOne({ category: "Hardware" }) db.post.find() 
  
 
db.post.deleteMany({ category: "Software" }) db.post.find() 
  
Conclusion: 


PRACTICAL-03 
Title: -Write a program to perform validation of a form using AngularJS. 
Programs: 
<!DOCTYPE html> 
<html> 
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"> </script>   
<body> 
 
<h2>Form Validation</h2> 
 
<form ng-app="myApp" ng-controller="validateCtrl" name="myForm" novalidate> 
 
<p>Username:<br> 
<input type="text" name="user" ng-model="user" required> 
<span style="color:red" ng-show="myForm.user.$dirty && myForm.user.$invalid"> 
<span ng-show="myForm.user.$error.required">Username is required.</span> 
</span> 
</p> 
 
<p>Email:<br> 
<input type="email" name="email" ng-model="email" required> 
<span style="color:red" ng-show="myForm.email.$dirty && myForm.email.$invalid"> 
<span ng-show="myForm.email.$error.required">Email is required.</span> 
<span ng-show="myForm.email.$error.email">Invalid email address.</span> 
</span> 
</p> 
 
<p> 
<input type="submit" ng-disabled="myForm.user.$dirty && myForm.user.$invalid ||   myForm.email.$dirty && myForm.email.$invalid"> 
</p> 
 
<p><br> 
  Pick a topic: 
  <input type="radio" ng-model="myVar" value="python">Python 
  <input type="radio" ng-model="myVar" value="android">Android 
  <input type="radio" ng-model="myVar" value="fullstack">Full Stack 
</p> 
 
<div ng-switch="myVar"> 
  <div ng-switch-when="python"> 
     <h1>Python</h1> 
     <p>Welcome to a world of Python.</p> 
  </div> 
  <div ng-switch-when="android"> 
     <h1>Android</h1> 
     <p>Welcome to a world of Android.</p> 
  </div> 
  <div ng-switch-when="fullstack"> 
     <h1>Full Stack</h1> 
     <p>Welcome to a world of Full Stack.</p> 
  </div> 
</div> 
</form> <script> var app = angular.module('myApp', []); app.controller('validateCtrl', function($scope) { 
    $scope.user = ''; 
    $scope.email = ' '; 
}); 
</script> 
</body> 
</html> 





Practical-04 
Title: -Write a program to create and implement modules and controllers in AngularJS. 
Programs: Main.js 
var AdditionApp = angular.module('AdditionApp',[]); 
AdditionApp.controller('DemoAddController', function($scope) { 
    $scope.add = function() { 
        $scope.n1=Number($scope.num1);         $scope.n2=Number($scope.num2);         return $scope.n1 + $scope.n2; 
    }; 
});    
     
var SubtractionApp = angular.module('SubtractionApp',[]); 
SubtractionApp.controller('DemoSubController', function($scope) { 
    $scope.sub = function() { 
        $scope.n1=Number($scope.num1);         $scope.n2=Number($scope.num2); 
        return $scope.n1 - $scope.n2; 
    }; 
}); 
 
var MultiplicationApp = angular.module('MultiplicationApp',[]); 
MultiplicationApp.controller('DemoMulController', function($scope) { 
    $scope.mul = function() { 
        $scope.n1=Number($scope.num1); 
        $scope.n2=Number($scope.num2); 
        return $scope.n1 * $scope.n2; 
    }; 
});    
     
var DivisionApp = angular.module('DivisionApp',[]); 
DivisionApp.controller('DemoDivController', function($scope) { 
    $scope.div = function() { 
        $scope.n1=Number($scope.num1);         $scope.n2=Number($scope.num2); 
        return $scope.n1 / $scope.n2; 
    }; 
}); 
 
add.html 
<!DOCTYPE html> 
<html> 
<head> 
    <meta charset="UTF-8"> 
    <title>Addition</title> 
    <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.4.8/angular.min.js"></script>     <script src="main.js"></script> 
</head> 
<body> 
<div ng-app = "AdditionApp" ng-controller="DemoAddController">     First Number: 
    <input type="text" ng-model="num1">     <br><br>     Second Number: 
    <input type="text" ng-model="num2"> 
    <br><br> 
    Addition :{{add()}} 
</div> 
</body> 
</html> 
 
sub.html <!DOCTYPE html> 
<html> 
<head> 
    <meta charset="UTF-8">     <title>Subtraction</title> 
    <script 
src="https://ajax.googleapis.com/ajax/libs/angularjs/1.4.8/angular.min.js"></script>     <script src="main.js"></script> 
</head> 
<body> 
<div ng-app = "SubtractionApp" ng-controller="DemoSubController">     First Number: 
    <input type="text" ng-model="num1">     <br><br>     Second Number: 
    <input type="text" ng-model="num2"> 
    <br><br> 
    Subtraction :{{sub()}} 
</div> 
</body> 
</html> 
 
mul.html <!DOCTYPE html> 
<html> 
<head> 
    <meta charset="UTF-8"> 
    <title>Multiplication</title> 
    <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.4.8/angular.min.js"></script>     <script src="main.js"></script> 
</head> 
<body> 
<div ng-app = "MultiplicationApp" ng-controller="DemoMulController">     First Number: 
    <input type="text" ng-model="num1">     <br><br>     Second Number: 
    <input type="text" ng-model="num2"> 
    <br><br> 
    Multiplication :{{mul()}} 
</div> 
</body> 
</html> 
 
div.html <!DOCTYPE html> 
<html> 
<head> 
    <meta charset="UTF-8"> 
    <title>Division</title> 
    <script 
src="https://ajax.googleapis.com/ajax/libs/angularjs/1.4.8/angular.min.js"></script>     <script src="main.js"></script> 
</head> 
<body> 
<div ng-app = "DivisionApp" ng-controller="DemoDivController">     First Number: 
    <input type="text" ng-model="num1">     <br><br>     Second Number: 
    <input type="text" ng-model="num2"> 
    <br><br> 
    Division :{{div()}} 
</div> 
</body> 
</html> 
 


Practical-05 
Title: -Write a program to implement Error Handling in Angular JS. 
Programs: 
<!DOCTYPE html> 
<html ng-app="studentApp"> 
<head> 
    <script 
src="https://ajax.googleapis.com/ajax/libs/angularjs/1.3.16/angular.min.js"></script> 
</head> 
<body class="container" ng-controller="studentController"> 
    Status: {{status}} <br /> 
    Data: {{data}} <br /> 
        <input type="button" value="Get Data" ng-click="getStudent()" /> 
    <script>         var app = angular.module('studentApp', []);         app.config(function ($provide) { 
            $provide.decorator('$exceptionHandler', function ($delegate) {                 return function (exception, cause) {                     $delegate(exception, cause);                     alert('Error occurred! Please contact admin.'); 
                }; 
            }); 
        }); 
        app.controller("studentController", function ($scope) {             var onSuccess = function (response) { 
                $scope.status = response.status; 
                $scope.data = response.data; 
SYBSc(CS) 	PRACTICAL-5 	AAD 
            }; 
            var onError = function (response) { 
                $scope.status = response.status; 
                $scope.data = response.data; 
            }; 
            $scope.getStudent = function () { 
                $http.get("/getdata").then(onSuccess, onError); 
            }; 
        }); 
    </script> 
</body> 
</html> 




Practical-07 
Title: -Create a simple HTML “Hello World” Project using AngularJS Framework and apply ng-controller, ng-model and expressions. 
Programs: 
<!DOCTYPE html>   
<html>   
<head>   
    <meta charset="utf 8"> 
    <title>Practical-8</title>      
</head>   
<body> 
    <div ng-app="app" ng-controller="HelloWorldCtrl">     Enter Message: 
    <input type="text" ng-model="message"><br><br> 
    <input type="button" name="submit" ng-click="msg()" value="Submit"><br><br> 
    <h1 ng-show="isVisible">{{message}}</h1> 
</div> 
<script src="https://code.angularjs.org/1.6.9/angular.js"></script> 
<script>       angular.module("app", []).controller("HelloWorldCtrl", function($scope) {   
        $scope.isVisible = false; 
        $scope.msg = function(){ 
            $scope.isVisible = true; 
 	        $scope.message; 
 	}; 
    } ) 
</script>  
SYBSc(CS) 	PRACTICAL-7 	AAD 
  
 	 
</body>   
</html> 
