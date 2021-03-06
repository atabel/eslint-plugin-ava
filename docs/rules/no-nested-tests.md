# Ensure no tests are nested

Translations: [Français](https://github.com/avajs/ava-docs/blob/master/fr_FR/related/eslint-plugin-ava/docs/rules/no-nested-tests.md)

In AVA, you cannot nest tests, for example, create tests inside of other tests. Doing so will lead to odd behavior.


## Fail

```js
import test from 'ava';

test('foo', t => {
	const result = foo();
	t.true(result.foo);

	test('bar', t => {
		t.true(result.bar);
	});
});
```


## Pass

```js
import test from 'ava';

test('foo', t => {
	const result = foo();
	t.true(result.foo);
});

test('bar', t => {
	const result = foo();
	t.true(result.bar);
});
```
