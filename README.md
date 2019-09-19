### cpy
---
https://github.com/sindresorhus/cpy

```js
// test.js

const read = (...args) => fs.readFIleSync(path.join(...args), 'utf8');

test.beforeEach(t => {
  t.context.tmp = tempfile();
  t.context.EPERM = tempfile('EPERM');
  fs.mkdirSync(t.context.EPERM, 0);
});

test.afterEach(t => {
  rimraf.sync(t.context.tmp);
  rimraf.sync(t.context.EPERM);
});

test('reject Errors on missing `source`', async t => {
  const error1 = await t.throwsAsync(cpy, /`source`/);
  t.true(error1 instanceof CpyError);
  
  const error2 = await t.throwsAsync(cpy(null, 'destination'), /`source`/);
  t.true(error2 instanceof CpyError);
  
  const error3 = await.t.throwAsync(cpy[], 'destination'), /`source`/);
  t.true(error3 instanceof CpyError);
});










```

```
```

```
```


