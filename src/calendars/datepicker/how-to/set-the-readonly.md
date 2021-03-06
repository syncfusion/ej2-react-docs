---
title: "How To"
component: "DatePicker"
description: "Miscellaneous aspects of customizing the date picker"
---

# Set the readonly

The following example demonstrates how to set `readonly` in DatePicker component.
You can achieve this by using `readonly` property.

{% tab template="datepicker/default", sourceFiles="app/**/*.tsx" %}

```typescript

// import the datepickercomponent
import { DatePickerComponent } from '@syncfusion/ej2-react-calendars';
import * as React from 'react';
import * as ReactDOM from 'react-dom';

export default class App extends React.Component<{}, {}> {

    private readonly: boolean = true;

    public render() {
        return (
            // specifies the tag for render the DatePicker component
            <DatePickerComponent readonly={this.readonly} placeholder="Enter date"/>
        );
     }
}

ReactDOM.render(<App />, document.getElementById('element'));

```

{% endtab %}