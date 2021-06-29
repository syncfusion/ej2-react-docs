---
title: "Date and Time masking"
component: "DateTimePicker"
description: "Miscellaneous aspects of customizing the datetimepicker"
---

# Enable the Masked Input

The DateTimePicker has built-in support to masking the date value, when `enableMask` property set as `true`.

To use mask support, inject the MaskedDateTime module in the DateTimePicker.

{% tab template="datetimepicker/mask-module", isDefaultActive = "true", sourceFiles="app/**/*.tsx" %}

```typescript

import * as ReactDOM from 'react-dom';
import * as React from 'react';
import { DateTimePickerComponent, Inject, MaskedDateTime } from '@syncfusion/ej2-react-calendars';
export default class App extends React.Component<{}, {}> {
    public render() {
        return <DateTimePickerComponent enableMask={true}> <Inject services={[MaskedDateTime]} /></DateTimePickerComponent>
    }
}

```

{% endtab %}

The mask pattern is defined based on the provided date format to the component. If the format is not specified, the mask pattern is formed based on the default format of the current culture.

The selected portions of date and time co-ordinates  can  be incremented and decremented using the Up/Down arrow keys. You can also use Right/Left arrow keys to navigate from one segment to another.

The following example demonstrates default and custom format of DateTimePicker component with mask module.

{% tab template="datetimepicker/mask-module", isDefaultActive = "true", sourceFiles="app/**/*.tsx" %}

```typescript

import * as ReactDOM from 'react-dom';
import * as React from 'react';
import { DateTimePickerComponent, Inject, MaskedDateTime } from '@syncfusion/ej2-react-calendars';
export default class App extends React.Component<{}, {}> {
    public render() {
       return (
            <div>
                {/* specifies the masked DateTimePicker component without format */}
                <DateTimePickerComponent enableMask={true}> <Inject services={[MaskedDateTime]} /></DateTimePickerComponent>
                <br />
                <br />

                {/* specifies the masked DateTimePicker component with format  */}
                <DateTimePickerComponent format='dd-MM-yyyy hh:mm a' enableMask={true}> <Inject services={[MaskedDateTime]} /></DateTimePickerComponent>
            </div>
        );

    }
}
```

{% endtab %}

# Configure Mask Placeholder

You can change mask placeholder value through property `maskPlaceholder`. By default , it takes the full name of date and time co-ordinates such as `day`, `month`, `year`, `hour` etc.

The following example demonstrates default and customized mask placeholder value.

{% tab template="datetimepicker/mask-module", isDefaultActive = "true", sourceFiles="app/**/*.tsx" %}

```typescript

import * as ReactDOM from 'react-dom';
import * as React from 'react';
import { DateTimePickerComponent, Inject, MaskedDateTime } from '@syncfusion/ej2-react-calendars';
export default class App extends React.Component<{}, {}> {
    private maskPlaceholderValue: object;
    constructor(props: {}) {
    super(props);
    this.maskPlaceholderValue = {day: 'd', month: 'M', year: 'y', hour: 'h', minute: 'm', second: 's'};
    }
    public render() {
       return (
            <div>
                {/* specifies the masked DateTimePicker component without mask placeholder */}
                <DateTimePickerComponent enableMask={true}> <Inject services={[MaskedDateTime]} /></DateTimePickerComponent>
                <br />
                <br />

                {/* specifies the masked DateTimePicker component with mask placeholder  */}
                <DateTimePickerComponent  enableMask={true} maskPlaceholder={this.maskPlaceholderValue}> <Inject services={[MaskedDateTime]} /></DateTimePickerComponent>
            </div>
        );

    }
}
```

{% endtab %}
