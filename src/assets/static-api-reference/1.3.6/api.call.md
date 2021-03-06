# call

This method wraps [`Meteor.call`](http://docs.meteor.com/#/full/meteor_call) method to run it's callback in a digestion
cycle so angular will detect the changes and update the views accordingly.

### Arguments

<table class="variables-matrix input-arguments">
    <thead>
    <tr>
        <th>Param</th>
        <th>Type</th>
        <th>Details</th>
        <th>Required</th>
    </tr>
    </thead>
    <tbody>
    <tr>
        <td><strong>name</strong></td>
        <td><a href="" class="label type-hint type-hint-string">String</a></td>
        <td><p>Name of method to invoke</p></td>
        <td>Yes</td>
    </tr>
    <tr>
        <td>arguments</td>
        <td><a href="" class="label type-hint type-hint-array">Any</a></td>
        <td><p>Optional arguments to send to method</p></td>
        <td>No</td>
    </tr>
    <tr>
        <td>callback</td>
        <td><a href="" class="label type-hint type-hint-function">Function</a></td>
        <td><p>Optional callback</p></td>
        <td>No</td>
    </tr>
    </tbody>
</table>

### Usage Example:

    myModule.controller('MyCtrl', ['$scope', '$reactive', function($scope, $reactive) {
      $reactive(this).attach($scope);

      this.call('add', 1, 2, (err, result) => {
        this.result = result;
      });
    }]);

> The example above will invoke the meteor method `add` with 1 and 2 as parameters. When the result arrives
arrives from the server, the callback method will run and then `angular-meteor` will run a digestive cycle
on the scope.
