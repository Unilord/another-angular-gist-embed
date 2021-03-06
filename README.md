# another-angular-gist-embed
Native Angular re-write of the [gist-embed project by blairvanderhoof](https://github.com/blairvanderhoof/gist-embed)

Enables you to include your gists in your angular projects. Since this is not a simply a wrapper but rather a re-write, it is completely integrated with the angular life-cycle. 
This module does not require jQuery as an external dependency.

##Demo
[Check it out](https://plnkr.co/edit/WgpS1MsxWr4FO80XAGlS?p=preview) 

##Getting started
Simply pick up the **another-angular-gist-embed.js** file in the **dist** folder and include it in your project source
then simply import the module into your project module

`angular.module('yourProject',['another-angular-gist-embed']);`

##Usage

To include a gist simply write a directive in your view with gist-id given in the option :

`<gist-embed data-gist-id="gistId"></code>`

you can also use the directive as an attribute :

`code gist-embed data-gist-id="gistId"></code>`

Here `gistId` is resolved to a value on the parent scope ( `$scope.gistId` )

##Examples

The directive takes all the options and use-cases supported by the gist-embed project. See [this for examples](http://blairvanderhoof.com/gist-embed/)

Below given are a few examples of usage.

**_Note : all the values given to attributes are interpolated with respect to the parent scope. The directive it self creates an isolate scope and therefore cannot be used with another directive on the same element._**

```<head>
<script>
  angular.module('example',['another-angular-gist-embed']);
  angular.module.controller('exampleCtrl',['$scope',function($scope){
    $scope.gistId = 'a85770344febb8e30935';
    $scope.range = '1,3-4';
    $scope.fileName = 'example-file2.html';
  }]);
</script>
</head>

<body>
  <div ng-controller=exampleCtrl"">
    <p>Loading a gist</p>
    <gist-embed data-gist-id="gistId"></gist-embed>
    
    <p>Loading a single line and a range of line numbers from a gist (line 1 and line 3 through 4)</p>
    <gist-embed data-gist-id="gistId" data-gist-line="range"></gist-embed>
    
    <p>Loading a single file from a gist (example-file2.html)</p>
    <code gist-embed data-gist-id="'5457644'" data-gist-file="fileName"></code>
    <!-- Note the usage of '' in the data-gist-id attribute.data-gist-id="'5457644'". We pass '5457644' as a string 
         because the statements between the double qoutes are interpolated
    -->
    
    <p>Loading a gist with both footer and line numbers removed</p>
    <code gist-embed data-gist-id="gistId" data-gist-hide-footer="true" data-gist-hide-line-numbers="true"></code>
  </div>
</body>
```
##Contributing
------
You should have node.js installed in your system.
Go into the directory where you want the project set up to be. Then :

1. `git clone https://github.com/kiran3807/another-angular-gist-embed.git`
2. `npm install`
3.  Create your feature branch (`git checkout -b my-new-feature`)
4.  Commit your changes (`git commit -am 'Add some feature'`)
5.  Push to the branch (`git push origin my-new-feature`)
6.  Create new Pull Request

For running test in watch mode : `npm test`

For creating a distributable file containing all of the code : `npm dist` (*this also runs all the tests for a single pass*)








