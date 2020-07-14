# svg-jest

This is a small library which transforms .SVG files for jest. It produces
and SVG in the stream which has two properties 'data-jest-file-name' which
includes the path and 'data-jest-name' which just the name portion.

Works with both of these formats:

```js
import MySvg from '../images/an-image.svg';
```
```js
import { ReactComponent as MySvg}  from '../images/an-image.svg';
```

The following JavaScript 
```js
const MyComponent = () => {
  return (
    <div>
	<MySvg/>
    </div>
  );
}
```
The resulting snapshot:

```html
<div>
    <AnImage/>
</div>
```

The resulting HTML:

```html
<div>
 <svg data-jest-file-name='an-image.svg' data-jest-name='an-image'/>
</div>
```

Any properties passed to '<MySvg>' are passed along into both the snapshot
and the resulting HTML.

# usage
Configure jest:

```json
{
    "jest": {
        "transform": {
            "\\.svg$": "svg-jest"
        }
    }
}
```
