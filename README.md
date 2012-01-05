miniglob : glob :: minimatch : fnmatch

This is a little thing for getting files from the filesystem that match
a glob pattern.

It has far fewer options than a full glob(3) implementation.

This is still very alpha.  Come back later for better tests and docs,
once it solidifies a bit more.

## Examples

```js
var miniglob = require('miniglob');

// find all the npm packages beneath the current directory
miniglob('**/package.json', function(err, matches) {
	console.log(matches);
});
```

If you want to locate a file in another directory, pass the `cwd` option:

```js
miniglob('**/package.json', { cwd: '/path/where/you/are/looking' }, function(err, matches) {
  console.log(matches);
});
```

miniglob also fires `match` events:

```js
miniglob('**/package.json').on('match', console.log);
```

and also `end` events:

```js
miniglob('**/package.json').on('end', function(matches) {
  console.log(matches);
});
```
