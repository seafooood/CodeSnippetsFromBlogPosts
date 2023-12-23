# How To Unit Test React Component using querySelector

In this example, we will Unit Test a React component using the function querySelector. The querySelector will find an elements based on CSS selectors.

## Procedure

- We are going to test a simple component called DemoQuerySelector. `npx create-react-app demo-query-selector`

- Change directory `cd demo-query-selector`

- Create file `DemoQuerySelector.js` in the `src` folder. Note that the div contains the id `id="current-selection"`.

```js
import React from 'react';

const DemoQuerySelector = () => (
  <div id="current-selection">
    Current selection = fred
  </div>
);

export default DemoQuerySelector;
```

- Create file `DemoQuerySelector.test.js` in the `src` folder. The unit test will find the div using the id attribue `id="current-selection"` and confirm the text contains the word "fred".

```js
import '@testing-library/jest-dom';
import { render, screen } from '@testing-library/react';
import DemoQuerySelector from './DemoQuerySelector';

test("Component renders text using container query", () => {
  // Arrange

  // Act
  render(<DemoQuerySelector />);

  // Assert
  const result = document.querySelector('#current-selection');
  expect(result).toHaveTextContent("fred");
});

```

- Run the unit test `npm test`
