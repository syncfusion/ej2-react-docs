---
title: "Date Masking"
component: "DatePicker"
description: "Miscellaneous aspects of customizing the date picker"
---

# Enable the Masked Input

The DatePicker has built-in support to masking the date value, when `enableMask` property set as `true`.

To use mask support, inject the MaskedDateTime module in the DatePicker.

{% tab template="datepicker/mask-module", isDefaultActive = "true", sourceFiles="app/**/*.tsx" %}

```typescript

import * as ReactDOM from 'react-dom';
import * as React from 'react';
import { DatePickerComponent, Inject, MaskedDateTime } from '@syncfusion/ej2-react-calendars';
export default class App extends React.Component<{}, {}> {
    public render() {
        return <DatePickerComponent enableMask={true}> <Inject services={[MaskedDateTime]} /></DatePickerComponent>
    }
}

```

{% endtab %}

The mask pattern is defined based on the provided date format to the component. If the format is not specified, the mask pattern is formed based on the default format of the current culture.

The selected portions of date and time co-ordinates  can  be incremented and decremented using the Up/Down arrow keys. You can also use Right/Left arrow keys to navigate from one segment to another.

The following example demonstrates default and custom format of DatePicker component with mask module.

{% tab template="datepicker/mask-module", isDefaultActive = "true", sourceFiles="app/**/*.tsx" %}

```typescript

import * as ReactDOM from 'react-dom';
import * as React from 'react';
import { DatePickerComponent, Inject, MaskedDateTime } from '@syncfusion/ej2-react-calendars';
export default class App extends React.Component<{}, {}> {
    public render() {
       return (
            <div>
                {/* specifies the masked DatePicker component without format */}
                <DatePickerComponent enableMask={true}> <Inject services={[MaskedDateTime]} /></DatePickerComponent>
                <br />
                <br />

                {/* specifies the masked DatePicker component with format  */}
                <DatePickerComponent format='dd-MM-yyyy' enableMask={true}> <Inject services={[MaskedDateTime]} /></DatePickerComponent>
            </div>
        );

    }
}
```

{% endtab %}

# Configure Mask Placeholder

You can change mask placeholder value through property `maskPlaceholder`. By default , it takes the full name of date and time co-ordinates such as `day`, `month`, `year`, `hour` etc.

The following example demonstrates default and customized mask placeholder value.

{% tab template="datepicker/mask-module", isDefaultActive = "true", sourceFiles="app/**/*.tsx" %}

```typescript

import * as ReactDOM from 'react-dom';
import * as React from 'react';
import { DatePickerComponent, Inject, MaskedDateTime } from '@syncfusion/ej2-react-calendars';
export default class App extends React.Component<{}, {}> {
    private maskPlaceholderValue: object;
    constructor(props: {}) {
    super(props);
    this.maskPlaceholderValue = {day: 'd', month: 'M', year: 'y'};
    }
    public render() {
       return (
            <div>
                {/* specifies the masked DatePicker component without mask placeholder */}
                <DatePickerComponent enableMask={true}> <Inject services={[MaskedDateTime]} /></DatePickerComponent>
                <br />
                <br />

                {/* specifies the masked DatePicker component with mask placeholder  */}
                <DatePickerComponent  enableMask={true} maskPlaceholder={this.maskPlaceholderValue}> <Inject services={[MaskedDateTime]} /></DatePickerComponent>
            </div>
        );

    }
}
```

{% endtab %}
