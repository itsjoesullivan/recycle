recycle
=======

```javascript
// Mutual

nameTag = function(page, model) {
  return json2html({
    ".name-tag": model.name
  });
};
```

```javascript
// Server-side

res.render = function(nameTag, data) {
  this.send(nameTag(data));
}

db.find(query, function(val) {
  res.render('index',val);
});
```

```javascript
// Client

View = Backbone.View.extend({
  initialize: function() {
    this.current = html2json(this.$el.html());
    this.model.on('change', function() {
      var patch = patch(this.current, this.render());
      this.apply(patch);
    });
  },
  render: function() {
    return nameTag(this.model.toJSON() );
  },
  apply: function(patch) {
  // patch may look like { ".name-tag": new String ("Joe") }
  // [ { remove: { "ul.app": { ".message-item": "Message" } } ]
  // Accomplished by: var ind = this.current["ul.app"].indexOf(obj); $("#app").children()[ind].remove()
  
  }
});

function patch(obj1,obj2) {
  // Return a diff of the object that can be applied to the html
}
```
