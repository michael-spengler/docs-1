# Events

When running, secure-rm emits events to let you know the progression of the deletion.

You can indeed intercept events for _each_ file.

```javascript
srm.event.on('mark', (file) => console.log('File / directory reached: ' + file))
srm.event.on('removed', (file) => console.log('File / directory removed: ' + file))

srm.event.on('done', (path) => console.log('Process done. ' + path))
```

