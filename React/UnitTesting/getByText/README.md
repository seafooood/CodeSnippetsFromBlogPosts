# How To Unit Test React Component using getByText

In this example, we will Unit Test a React component using the function getByText. The getByText will confim if the element contains the given text.

## Procedure

- We are going to test a simple component called DemoGetByTestId. `npx create-react-app demo-get-by-text`

- Change directory `cd demo-get-by-text`

- Create file `DemoGetByText.js` in the src folder.

```js
const DemoGetByText = ({temperature}) => (
    <div>{temperature > 23 ? "too hot" : "too cold"</div>
  );
  
export default DemoGetByText;
```

- Create file `DemoGetByText.test.js` in the src folder. The unit test confirm if the component conains the text "too hot" or "too cold".

```js
import '@testing-library/jest-dom';
import { render, screen } from '@testing-library/react';
import DemoGetByText from './DemoGetByText';

// Test confirms that the div will contain the text "too hot"
test("Component renders text too hot", () => {
    // Arrange
    const temperature = 40

    // Act
    render(<DemoGetByText temperature={temperature}/>);

    // Assert
    const result = screen.getByText('too hot');
    expect(result).not.toBeNull();
});

// Test confirms that the div will contain the text "too cold"
test("Component renders text too cold", () => {
    // Arrange
    const temperature = 10
    
    // Act
    render(<DemoGetByText temperature={temperature}/>);

    // Assert
    const result = screen.getByText('too cold');
    expect(result).not.toBeNull();
});
```

- Run the unit test `npm test`
