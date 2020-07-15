# svg-jest


This is a small library which transforms .SVG files for jest. It produces
and SVG in the stream.

The transformed item will have the following properties on it.
* data-jest-file-name: The name of the file (e.g. 'some-image.svg')
* data-jest-svg-name: Only the name portion of the file (e.g. 'some-image')
* data-testid: Same as data-jest-svg-name, but works with @testing-library/react getByTestId()

Works with both of these formats:

```js
import MySvg from '../images/an-image.svg';

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
 <svg data-jest-file-name='an-image.svg' data-jest-svg-name='an-image' data-testid='an-image'/>
</div>
```

In additoin, any properties passed to '<MySvg>' are passed along into both the snapshot
and the resulting trees.

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
