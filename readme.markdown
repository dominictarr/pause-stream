# PauseStream

This is a `Stream` that will strictly buffer when paused.
Connect it to anything you need buffered.

```
  var pause = require('pause-stream')();
  pause.pause()
  badlyBehavedStream.pipe(pause)

  aLittleLater(function (err, data) {

    pause.pipe(createAnotherStream(data))
    pause.resume()

  })

```

`PauseStream` will buffer whenever paused.
it will buffer when yau have called `pause` manually.
but also when it's downstream `dest.write()===false`.
it will attempt to drain the buffer when you call resume
or the downstream emits `'drain'`
