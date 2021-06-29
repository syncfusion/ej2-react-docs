---
title: "Time masking"
component: "TimePicker"
description: "Miscellaneous aspects of customizing the TimePicker"
---

# Enable the Masked Input

The TimePicker has built-in support to masking the time value, when `enableMask` property set as `true`.

To use mask support, inject the MaskedDateTime module in the TimePicker.

{% tab template="timepicker/mask-module", isDefaultActive = "true", sourceFiles="app/**/*.tsx" %}

```typescript

import * as ReactDOM from 'react-dom';
import * as React from 'react';
import { TimePickerComponent, Inject, MaskedDateTime } from '@syncfusion/ej2-react-calendars';
export default class App extends React.Component<{}, {}> {
    public render() {
        return <TimePickerComponent enableMask={true}> <Inject services={[MaskedDateTime]} /></TimePickerComponent>
    }
}

```

{% endtab %}

The mask pattern is defined based on the provided time format to the component. If the format is not specified, the mask pattern is formed based on the default format of the current culture.

The selected portions of date and time co-ordinates  can  be incremented and decremented using the Up/Down arrow keys. You can also use Right/Left arrow keys to navigate from one segment to another.

The following example demonstrates default and custom format of TimePicker component with mask module.

{% tab template="timepicker/mask-module", isDefaultActive = "true", sourceFiles="app/**/*.tsx" %}

```typescript

import * as ReactDOM from 'react-dom';
import * as React from 'react';
import { TimePickerComponent, Inject, MaskedDateTime } from '@syncfusion/ej2-react-calendars';
export default class App extends React.Component<{}, {}> {
    public render() {
       return (
            <div>
                {/* specifies the masked TimePicker component without format */}
                <TimePickerComponent enableMask={true}> <Inject services={[MaskedDateTime]} /></TimePickerComponent>
                <br />
                <br />

                {/* specifies the masked TimePicker component with format  */}
                <TimePickerComponent format='h:mm a' enableMask={true}> <Inject services={[MaskedDateTime]} /></TimePickerComponent>
            </div>
        );

    }
}
```

{% endtab %}

# Configure Mask Placeholder

You can change mask placeholder value through property `maskPlaceholder`. By default , it takes the full name of  time co-ordinates such as `hour`, `minute` and `second`.

The following example demonstrates default and customized mask placeholder value.

{% tab template="timepicker/mask-module", isDefaultActive = "true", sourceFiles="app/**/*.tsx" %}

```typescript

import * as ReactDOM from 'react-dom';
import * as React from 'react';
import { TimePickerComponent, Inject, MaskedDateTime } from '@syncfusion/ej2-react-calendars';
export default class App extends React.Component<{}, {}> {
    private maskPlaceholderValue: object;
    constructor(props: {}) {
    super(props);
    this.maskPlaceholderValue = { hour: 'h', minute: 'm', second: 's' };
    }
    public render() {
       return (
            <div>
                {/* specifies the masked TimePicker component without mask placeholder */}
                <TimePickerComponent enableMask={true}> <Inject services={[MaskedDateTime]} /></TimePickerComponent>
                <br />
                <br />

                {/* specifies the masked TimePicker component with mask placeholder  */}
                <TimePickerComponent  enableMask={true} maskPlaceholder={this.maskPlaceholderValue}> <Inject services={[MaskedDateTime]} /></TimePickerComponent>
            </div>
        );

    }
}
```

{% endtab %}
