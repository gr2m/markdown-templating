# `markdown-templating`

Not much to see here yet. It's just a place for me to experiment with a templating syntax for markdown files.

## Example

Given this template

```md
<!--YAML:meta
-->

### Some title

<!--START:block_content-->
<!--END:block_content-->

Baz, <!--START:inline_content--><!--END:inline_content-->, daz.

<!--START:some_var-->
<!--END:some_var-->
```

And this data:

```js
{
  meta: { foo: "bar", baz: "daz" },
  block_content: { content: "This is the value of the `block_content` variable" },
  inline_content: { content: "value of `inline_content` variable" },
  some_var: { checksum: "abcd567", content: "This is the value of the `block_content` variable" },
}
```

The resulting markdown text would be

```md
<!--YAML:meta
foo: bar
baz: daz
-->

### Some title

<!--START:block_content-->
This is the value of the `block_content` variable
<!--END:block_content-->

Baz, <!--START:inline_content-->value of `inline_content` variable<!--END:inline_content-->, daz.

<!--START:some_var (checksum="abcd567")-->
This is the value of the `block_content` variable
<!--END:some_var-->
```

The resulting markdown text could in turn be parsed back into the same data.

## License 

MIT