---
title: [Push data using REST APIs]
last_updated: 3/3/2021
summary: "You can use the REST APIs to push data to a third-party application."
sidebar: mydoc_sidebar
permalink: /:collection/:path.html
---

ThoughtSpot allows you to push data to a third-party application from the ThoughtSpot application context through an API service.

For example, if your client application has embedded the ThoughtSpot search functionality, you can initiate an action to send a search answer to another application or a workflow. To do this, you can use the custom menu item configured for your embedded instance.

For more information on custom menu items, see [add custom actions]({{ site.baseurl }}/admin/ts-cloud/customize-actions-spotdev.html).

## Data format

The data is available to the external application in JSON (JavaScript Object Notation) format. You must parse the JSON to get the data values you need using JavaScript in the receiving application.

## Sample application

Here is a sample application for pushing data from an embedded ThoughtSpot instance:

``` HTML
<!doctype html>
<html lang="en">
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<script type="text/javascript" src="api/api.js"></script>
<body>
    <script>

        var app = angular.module("latestData", []);
        app.controller("dataCtrl", ['$scope', '$window', function($scope, $window) {

            $scope.currentData=undefined;
            $scope.showData=false;
            $scope.displayData = function() {
                $scope.showData = true;
            };
            function currentDataCallback(event) {
                $scope.currentData = event;
            }
            $window.onload = function(){
                $window.thoughtspot.getCurrentData(currentDataCallback);
            };

        }]);
    </script>
    <div ng-app ="latestData" ng-controller="dataCtrl">
        <button class="get-data" ng-click="displayData()">Click here for latest exported data</button>
        <div class="display-data" ng-if="showData"> {{currentData}}</div>
    </div>
</body>
</html>
```