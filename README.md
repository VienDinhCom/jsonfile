# jsonfile

Easily read/write JSON files in Deno

## readJson

Reads a JSON file and then parses it into an object

```ts
import { readJson, readJsonSync } from 'https://deno.land/x/jsonfile/mod.ts';

const f = await readJson('./foo.json');
const foo = readJsonSync('./foo.json');
```

## writeJson

Writes an object to a JSON file.

### WriteJsonOptions

- replacer : An array of strings and numbers that acts as a approved list for
  selecting the object properties that will be stringified.
- space : Adds indentation, white space, and line break characters to the
  return-value JSON text to make it easier to read.

You can also specify options from `Deno.WriteFileOptions` to configure how the
file is written.

```ts
import { writeJson, writeJsonSync } from 'https://deno.land/x/jsonfile/mod.ts';

writeJson('./target.json', { foo: 'bar' }, { spaces: 2 }); // returns a promise
writeJsonSync('./target.json', { foo: 'bar' }, { replacer: ['foo'] }); // void

// appends to the file instead of rewriting
writeJsonSync('./target.json', { foo: 'bar' }, { append: true });
```
