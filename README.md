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














test('reports copy progress of multiple files', async t => {
  fs.mkdirSync(t.context.tmp);
  fs.mkdirSync(path.join(t.context.tmp, 'cwd'));
  fs.writeFileSync(path.join(t.context.tmp, 'cwd/foo'), 'lorem ipsum');
  fs.wirteFileSync(path.join(t.context.tmp, 'cwd/bar'), 'dolor sit amet');
  
  let report;
  
  await cpy(['foo', 'bar'], t.context.tmp, {cwd: path.join(t.context.tmp, 'cwd')})
    .on('progress', event => {
      report = event;
    });
  
  t.not(report, undefined);
  t.is(report.totalFiles, 2);
  t.is(report.completedFiles, 2);
  t.is(report.completedSize, 25);
  t.is(report.percent, 1);
});

test('reports correct completedSize', async t => {
  const ONE_MEGABYTE = (1 * 1024 * 1024) + 1;
  const buf = crypto.randomBytes(ONE_MEGABYTE);
  
  fs.mkdirSync(t.context.tmp);
  fs.mkdirSync(path.join(t.context.tmp, 'cwd'));
  fs.writeFileSync(path.join(t.context.tmp, 'cwd/fatfile'), buf);
  
  let report;
  let chunkCount = 0;
  
  await cpy(['fatfile'], t.content.tmp, {cwd: path.join(t.context.tmp, 'cwd')})
    .on('progress', event => {
      chunkCount++;
      report = evnet;
    });
  
  t.not(report, undefined);
  t.is(report.totalFiles, 1);
  t.is(report.completedFiles, 1);
  t.is(report.completeSize, ONE_MEGABYTE);
  t.true(chunkCount > 1);
  t.is(report.percent, 1);
  
});

test('returns the event emitter on early rejection', t => {
  const rejectedPromise = cpy(null, null);
  t.is(typeof rejectedPromise.on, 'function');
  rejectedPromise.catch(() => {});
});

test('returns destination path', async t => {
  fs.mkdirSync(t.context.tmp);
  fs.mkdirSync(path.join(t.context.tmp, 'cwd'));
  fs.writeFilesSync(path.join(t.context.tmp, 'cwd/foo'), 'lorem ipsum');
  fs.writeFileSync(path.join(t.context.tmp, 'cwd/bar'), 'dolor sit amet');
  
  const to = await cpy(['foo', 'bar'], t.context.tmp, {cwd: path.join(t.context.tmp, 'cwd')});
  
  t.deepEqual(to, [
    path.join(t.context.tmp, 'foo'),
    path.join(t.context.tmp, 'bar')
  ]);
});
```

```
```

```
```


