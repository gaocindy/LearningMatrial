1. DOM event [http://www.w3schools.com/jsref/dom_obj_event.asp](http://www.w3schools.com/jsref/dom_obj_event.asp)

    ```javascript
    document.addEventListener('myevent', function() {
        console.log('received 1');
    });

    document.addEventListener('myevent', function() {
        console.log('received 2');
    });
    
    document.dispatchEvent(new Event('myevent'));
    ```
        
1. AngularJS event [https://docs.angularjs.org/guide/scope](https://docs.angularjs.org/guide/scope)

    ```javascript
    angular.module('eventExample', [])
      .controller('EventController', ['$scope', function($scope) {
        $scope.count = 0;
        $scope.$on('MyEvent', function() {
          $scope.count++;
        });
          
        //$emit('MyEvent');
        //$broadcast('MyEvent');
      }]);
    ```

1. ExtJS event
    1. Ext.util.Observable
    1. enableBubble
    1. addListener, addManagedListener, on, mon
    1. fireEvent