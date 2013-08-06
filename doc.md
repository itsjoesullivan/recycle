```javascript
res.render('index',model);
```

```javascript
var inner = document.getElementById("#app");
view.set('current',html2json(inner));
view.model.on('change', function() {
});
view.initialize = function() {
	this.update();	
};
update = function() {
	var patch = diff(this.get('current'),this.render());
	this.apply(patch);
}
```

```
template = function(model) {
	return json2html({
		".name-tag": model.name
	});
};
render = function(template,model) {
	return template(model);	
};

```
