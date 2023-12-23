# How To Create a Combobox React Component With Unit Tests

In this article we will create a React component that displays a Combobox. The values of the combobox are set from an array. We will also create unit test to confirm the components functionality. 

## Component Setup

- create the app `npx create-react-app demo-select`.
- Change directory `cd demo-select`.
- Create a directory within `src` called `components`.
- Create a file called `DemoSelect.js` withing the components directory.

```js
import {useState} from 'react'

const DemoSelect = ({optionList}) => {
    const [selection, setSelection] = useState(optionList[0]);

    return (
        <div>
            <p>Demo Selector</p>
            <select 
                value={selection}
                onChange={(event) => setSelection(event.target.value)}
            >
                {optionList.map(t=><option value={t} key={t}>{t}</option>)}
            </select>
            <div data-testid="current-selection">Current selection = {selection}</div>
        </div>
    );
}

export default DemoSelect;

```

- Create a file called `DemoSelect.test.js`

```js
import '@testing-library/jest-dom';
import { render, screen } from '@testing-library/react';
import DemoSelect from './DemoSelect';

// Test confirms the default selection matches the first option 
test("Component renders default selection", () => {
    // Arrange
    const optionOne = "apple";
    const optionTwo = "orange";
    const optionList = [optionOne, optionTwo];

    // Act
    render(<DemoSelect optionList={optionList} />);

    // Assert
    const result = screen.getByTestId('current-selection');
    expect(result).toHaveTextContent(optionOne);
});

// Test confirms that the select contains the correct number of options
test("Component has correct number of options", () =>{
    // Arrange
    const optionOne = "apple";
    const optionTwo = "orange";
    const optionList = [optionOne, optionTwo];

    // Act
    render(<DemoSelect optionList={optionList} />);

    // Assert
    const result = screen.getByRole('combobox');
    expect(result.length).toBe(optionList.length);
});


// Test confirms that the select contains options from the list
test("Component contains options from list", () =>{
    // Arrange
    const optionOne = "apple";
    const optionTwo = "orange";
    const optionList = [optionOne, optionTwo];

    // Act
    render(<DemoSelect optionList={optionList} />);

    // Assert
    const result = screen.getByRole('combobox');
    expect(result.length).toBe(optionList.length);
    expect(result.options[0].text).toBe(optionOne);
    expect(result.options[1].text).toBe(optionTwo);
});


```

- Run the tests `npm test`

- To use the component add an include line to your project file eg `import DemoSelect from './DemoSelect';`. Create a list of options eg `const optionList = ["apple", "orange"];`, create an instance of the component and pass the list to the component `<DemoSelect optionList={optionList} />`.
 