# List of Patterns Found while practicing for coding internviews


* This doc is to take a few minutes at the end of each problem to remember 
the moments where I got stuck, the things I  had trouble 
figuring out and the things you got wrong at first. Basically, 
what _approaches_ you learned, that you can apply to future questions.


----

### Patterns

##### 5/30/17
* Problem: Understood how to solve the problem, but identifying the JS function that would assist is in rounding numbers didn't come. 
    * Solution: use `parseInt()` and `%` (modulus)
   
    
##### 6/13/17
    
*  Problem: trying to check to see if a string was a palindrome and it was passing test cases
      * Solution/Fix: I was using a single equals and assigning a variable instead of using double equals
      
      
##### 7/14/17

######Pattern 1 - Passing props from a parent component to grandchildren (USE React.CloneElement)
* Issue: was creating a Checkbox group component and having issue figuring out how to pass all the props that the checkbox needs down through the group component and into the child of the group
* Fix: Instead of trying manicure the Checkbox group to pass every single prop you pass in `children` as props and then map over it using `React.Children.map`
and then you return    `React.cloneElement(child)`. See below for an example:

````
render() {
        const {children, selectedOption, legend} = props;
        const radioButtons = React.Children.map(children, (child) => {
            return (
                <li>
                    {React.cloneElement(child,
                        {
                            id: child.props.id,
                            label: child.props.label,
                            checked: selectedOption === child.props.option,
                            disabled: child.props.disabled,
                            onChange: child.props.onChange,
                        }
                    )}
                </li>
            );
        });

       return (
            <fieldset className=“usa-fieldset-inputs”>
                <legend className=“usa-sr-only”>{legend}</legend>
                <ul className=“usa-unstyled-list”>
                    {radioButtons}
                </ul>
            </fieldset>
        );
    }
````      