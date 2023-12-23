# How To Unit Test React Component using getByTestId

In this example, we will Unit Test a React component using the function getByTestId. The getByTestId will find an element from the DOM using the attribute data-testid.

## Procedure

- We are going to test a simple component called DemoGetByTestId. `npx create-react-app demo-get-by-test-id`

- Change directory `cd demo-get-by-test-id`

- Create file `DemoGetByTestId.js`.Note that the div contains the attribue `data-testid="current-selection"`.

```js
const DemoGetByTestId = () => (
    <div data-testid="current-selection">Current selection = fred</div>
  );
  
export default DemoGetByTestId;
```

- Create file `DemoGetByTestId.test.js`. The unit test will find the div using the attribue `data-testid="current-selection"` and confirm the text contains the word "fred".

```js
import '@testing-library/jest-dom';
import { render, screen } from '@testing-library/react';
import DemoGetByTestId from './DemoGetByTestId';

// Test confirms that the div with the test id 'current-selection' contains the test "fred"
test("Component renders text", () => {
    // Arrange

    // Act
    render(<DemoGetByTestId/>);

    // Assert
    const result = screen.getByTestId('current-selection');
    expect(result).toHaveTextContent("fred");
});
```

- Run the unit test `npm test`
