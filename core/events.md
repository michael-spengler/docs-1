# Events

When running, secure-rm emits events to let you know the progression of the deletion.

You can indeed intercept error and ending events for _each_ file.

```javascript
srm.event.on('start', (file) => console.log('Starting ' + file))
srm.event.on('done', (file) => console.log('Done ' + file))

srm.event.on('info', (file, info) => console.log('Info ' + info + file))

srm.event.on('warn', (file, err) => console.log('Warning ' + err + file))
srm.event.on('error', (file, err) => console.log('Error ' + err + file))
```

