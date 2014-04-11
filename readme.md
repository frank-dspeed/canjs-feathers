# CanJS Feathers [![Build Status](https://travis-ci.org/feathersjs/canjs-feathers.png?branch=master)](https://travis-ci.org/feathersjs/canjs-feathers)

> CanJS model implementation that connects to Feathers services through a real-time socket.

## Getting Started

The easiest way to obtain the plugin is through Bower:

> bower install canjs-feathers

Or [download the JavaScript]() and put it in your CanJS project folder.

Once set up you have to connect to the Feathers server:

```js
// connects to the current host via SocketIO
can.Feathers.connect();
// connects to todos.feathersjs.com
can.Feathers.connect('http://todos.feathersjs.com');
// connect to my.app.com using Primus
can.Feathers.connect({
  host: 'http://my.app',
  type: 'primus'
});
```

To create a model you can use the shorthand `can.Feathers.model`:

```js
// connects to the todos service
var Todo = can.Feathers.model('/todos');
```

Or extend `can.Feathers.Model` and set the `service` static property:

```js
var Todo = can.Feathers.Model.extend({
  service: 'todos'
}, {});
```

Now you can use it like any other [CanJS](http://canjs.com/docs/can.Model.html) model:

```js
var todo = new Todo({ description: 'You have to do dishes' });

todo.save();

Todo.findAll().then(function(todos) {
  console.log(todos);
});
```

## Author

- [David Luecke](https://github.com/daffl)

## License

Copyright (c) 2014 David Luecke

Licensed under the [MIT license](LICENSE).