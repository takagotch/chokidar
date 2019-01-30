### chokidar
---
https://github.com/paulmillr/chokidar

```
npm install chokidar --save
```

```js
var chokidar = require('chokidar');
chokidar.watch('.'. {ignored: /(^|[\/\\])\../}).on('all', (event, path) => {
  console.log(event, path);
});

var watcher = chokidar.watch('file, dir, glob, or array', {
  ignored: /(^|[\/\\])\../,
  persistent: true
});

var log = chokidar.log.bind(console);
watcher
  .on('add', path => log(`File ${path} has been added`))
  .on('change', path => log(`File ${path}`) has been changed)
  .on('unlink', path => log(`File ${path} has been removed`));
watcher
  .on('addDir', path => log(`Directory ${path} has been added`))
  .on('unlinkDir', path => log(`Directory ${path} has been removed`))
  .on('error', error => log(`Watcher error: ${error}`))
  .on('ready', () => log('Initial scan complete. Ready for changes'))
  .on('raw', (event, path, detail) => {
    log('Raw event info:', event, path, details);
  });
watcher .on('change', (path, stats) => {
  if(stats) console.log(`File ${path} changed size to ${stats.size}`);
});
watcher.add('new-file');
watcher.add(['new-file-2', 'new-file-3', '**/other-file*']);
var watchedPaths = watcher.getWatched();
watcher.unwatch('new-file*');
watcher.close();
chokidar.watch('file', {
  persistent: true,
  ignored: '*.txt',
  followSymlinks: true,
  cwd: '.',
  disableGlobing: false,
  usePolling: true,
  interval: 100,
  binaryInterval: 300,
  alwaysStat: false,
  depth: 99,
  awaitWriteFinish: {
    stabilityThreshold: 2000,
    pollInterval: 100
  },
  ignorePermissionErrors: false,
  atomic: true
});
```


