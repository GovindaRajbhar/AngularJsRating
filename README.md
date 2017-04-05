# AngularJsRating
Simple AngularJs Rating

There n number of Angularjs rating examples are there but here I have impelemented as simple as I can implement.

Simple implementation
------------------------------------------------------------------------------------------------------------------------------
Angular Code

var starApp = angular.module('starApp', []);

starApp.controller('StarCtrl', ['$scope', function ($scope) {
    $scope.rating = { current: 3, max: 5 };
}]);

starApp.directive('starRating', function () {
    return {
        restrict: 'A',
        template: '<ul class="rating">' +
            '<li ng-repeat="star in stars" ng-class="star">' +
            '\u2605' +
            '</li>' +
            '</ul>',
        scope: {
            ratingValue: '=',
            max: '='
        },
        link: function (scope, elem, attrs) {
            scope.stars = [];
            for (var i = 0; i < scope.max; i++) {
                scope.stars.push({
                    filled: i < scope.ratingValue
                });
            }
        }
    }
});
 
----------------------------------------------------------------------------------------------------------------------- 
HTML Part
<body ng-app="starApp">
    <div ng-controller="StarCtrl">
        <div>
            {{rating.current}} out of {{rating.max}}
            <div star-rating rating-value="rating.current" max="rating.max"></div>
        </div>
    </div>
</body>
