Usage
=====

Require `computed_attributes` after backbone.

A `compute` method is added to your models.
Pass in a name for the attribute and a function used to compute it:

```javascript
var Person = Backbone.Model.extend({
  initialize: function() {
    this.compute('full_name', function() {
      this.get('first_name') + ' ' + this.get('last_name');
    });
  }
});

var bob = new Person({first_name: "Bob", last_name: "Evans"});

bob.get('full_name'); //=> "Bob Evans"
bob.set('last_name', 'Marley');
bob.get('full_name');  //=> "Bob Marley"
```

In coffeescript:


```coffee
class Person extends Backbone.Model
  initialize: ->
    @compute 'full_name', ->
      "#{@get 'first_name'} #{@get 'last_name'}"
```

`full_name` will automatically be re-computed when you change
`first_name` or `last_name`.

Note that `compute` only knows about the attributes that are actually accessed
inside the computing function.
