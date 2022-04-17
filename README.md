# rollup-build-demo

when build `@elastic/apm-rum-core` by rollup, function `patchEventTarget` will be removed.

source file: 

```javascript
function patchAll() {
  if (!alreadyPatched) {
    alreadyPatched = true;
    patchXMLHttpRequest(function (event, task) {
      patchEventHandler.send(XMLHTTPREQUEST, [event, task]);
    });
    patchFetch(function (event, task) {
      patchEventHandler.send(FETCH, [event, task]);
    });
    patchHistory(function (event, task) {
      patchEventHandler.send(HISTORY, [event, task]);
    });
    patchEventTarget(function (event, task) {
      patchEventHandler.send(EVENT_TARGET, [event, task]);
    });
  }

  return patchEventHandler;
}
```

dist file

```javascript
function patchAll() {
  if (!alreadyPatched) {
    alreadyPatched = true;
    patchXMLHttpRequest(function (event, task) {
      patchEventHandler.send(XMLHTTPREQUEST, [event, task]);
    });
    patchFetch(function (event, task) {
      patchEventHandler.send(FETCH, [event, task]);
    });
    patchHistory(function (event, task) {
      patchEventHandler.send(HISTORY, [event, task]);
    });
    // patchEventTarget disappear...
  }

  return patchEventHandler;
}
```
