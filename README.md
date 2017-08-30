# angular-basemodel
Injectable base model for restful apis

Requires angular & underscore or lodash

bower install angular-basemodel --save

Example:
```
angular.module('baseModelExample', [
            'angular-basemodel',
        ]).run(function($rootScope, jsonTestModel){
            var jsonTestModel = new jsonTestModel();
            jsonTestModel.getKeyValue().success(function(data){
                $rootScope.result = data.result;
                console.log('key2', data.key2);
            })
        }).factory('jsonTestModel', function($rootScope, $baseModel){
              return function(){
                  var model = angular.extend(new $baseModel(), {});
                  model.url = "http://echo.jsontest.com/";
                  model.getKeyValue = function(){
                      model.route="result/success/key2/win";
                      return model.get();
                  }
                  return model;
              }
          });
```
