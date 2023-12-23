# How To Unit Test React Component using getByRole

In this example, we will Unit Test a React component using the function getByRole. The getByTestId is useful if the div has a specific role, you can use getByRole. This is particularly useful for semantic HTML where elements have roles like "button," "checkbox," etc.

## Procedure

- We are going to test a simple component called DemoGetByRole. `npx create-react-app demo-get-by-role`

- Change directory `cd demo-get-by-role`

- Create file `DemoGetByRole.js` in the `src` folder. Note that the component contain three different buttons.

```js
const DemoGetByRole = () => (
    <div>
        <button>Button One</button>
        <button>Button Two</button>
        <button>Button Three</button>
    </div>
  );
  
export default DemoGetByRole;
```

- Create file `DemoGetByRole.test.js` in the `scr` folder. The unit test will find second button.

```js
import '@testing-library/jest-dom';
import { render, screen } from '@testing-library/react';
import DemoGetByRole from './DemoGetByRole';

test("Component renders button", () => {
    // Arrange
    const expectedText = "Button Two"; 

    // Act
    render(<DemoGetByRole/>);

    // Assert
    const result = screen.getByRole('button', { name: expectedText });
    expect(result).toHaveTextContent(expectedText);
});
```

- Run the unit test `npm test`
