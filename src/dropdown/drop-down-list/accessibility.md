---
title: "Drop-down list Accessibility"
component: "DropDownList"
description: "This section for Syncfusion react drop-down list component explains the WAI-ARIA accessibility support."
---

# Accessibility

The DropDownList component has been designed, keeping in mind the `WAI-ARIA` specifications, and applies
the WAI-ARIA roles, states, and properties along with `keyboard support`. This component is characterized
by complete keyboard interaction support and ARIA accessibility support that makes it easy for people who
use assistive technologies (AT) or those who completely rely on keyboard navigation.

## ARIA attributes

The DropDownList component uses the `Listbox` role, and each list item has an `option` role. The following
`ARIA attributes` denote the DropDownList state.

| **Properties** | **Functionalities** |
| --- | --- |
| aria-haspopup | Indicates whether the DropDownList input element has a popup list or not. |
| aria-expanded | Indicates whether the popup list has expanded or not. |
| aria-selected | Indicates the selected option. |
| aria-readonly | Indicates the readonly state of the DropDownList element. |
| aria-disabled | Indicates whether the DropDownList component is in a disabled state or not. |
| aria-activedescendent | This attribute holds the ID of the active list item  to focus its descendant child element. |
| aria-owns | This attribute contains the ID of the popup list to indicate popup as a child element. |

## Keyboard interaction

You can use the following key shortcuts to access the DropDownList without interruptions.

| **Keyboard shortcuts** | **Actions** |
| --- | --- |
| <kbd>Arrow Down</kbd> | Selects the first item in the DropDownList when no item selected. Otherwise, selects the item next to the currently selected item. |
| <kbd>Arrow Up</kbd> | Selects the item previous to the currently selected one. |
| <kbd>Page Down</kbd> | Scrolls down to the next page and selects the first item when popup list opens. |
| <kbd>Page Up</kbd> | Scrolls up to the previous page and selects the first item when popup list opens. |
| <kbd>Enter</kbd> | Selects the focused item, and when it is in an open state the popup list closes. Otherwise, toggles the popup list. |
| <kbd>Tab</kbd> | Focuses on the next TabIndex element on the page when the popup is closed. Otherwise, closes the popup list and remains the focus of the component. |
| <kbd>Shift + tab </kbd> | Focuses on the previous TabIndex element on the page when the popup is closed. Otherwise, closes the popup list and remains the focus of the component. |
| <kbd>Alt + Down</kbd> | Opens the popup list. |
| <kbd>Alt + Up</kbd> | Closes the popup list. |
| <kbd>Esc(Escape)</kbd> | Closes the popup list when it is in an open state and the currently selected item remains the same. |
| <kbd>Home</kbd> | Selects the first item. |
| <kbd>End</kbd> | Selects the last item. |

> In the below sample, <kbd>alt+t</kbd> keys are used to focus the DropDownList component.

{% tab template="dropdownlist/basic", sourceFiles="app/**/*.tsx,index.html", isDefaultActive=true %}

```typescript

import { DropDownListComponent } from '@syncfusion/ej2-react-dropdowns';
import * as React from 'react';
import * as ReactDOM from 'react-dom';

export default class App extends React.Component<{}, {}> {
    // defined the array of data
    private gameList: { [key: string]: Object }[] = [
        { Id: 'Game1', Game: 'Badminton' },
        { Id: 'Game2', Game: 'Basketball' },
        { Id: 'Game3', Game: 'Cricket' },
        { Id: 'Game4', Game: 'Football' },
        { Id: 'Game5', Game: 'Golf' },
        { Id: 'Game6', Game: 'Hockey' },
        { Id: 'Game7', Game: 'Rugby' },
        { Id: 'Game8', Game: 'Snooker' },
        { Id: 'Game9', Game: 'Tennis' }
    ];

    // maps the appropriate column to fields property
    private fields: object = { text: 'Game', value: 'Id' };

    // instance of DropDownList component
    private dropDownListObj: any;

    public componentDidMount() {
        const proxy = this;
        document.onkeyup = (e) => {
            if (e.altKey && e.keyCode === 84 /* t */) {
                // press alt+t to focus the control.
                proxy.dropDownListObj.inputElement.focus();
            }
        };
    }

    public render() {
        return (
            // specifies the tag for render the DropDownList component
            <DropDownListComponent id="ddlelement" ref={(scope) => { this.dropDownListObj = scope; }} popupHeight='200px' fields={this.fields} dataSource={this.gameList} placeholder="Select a game" />
        );
    }
}
ReactDOM.render(<App />, document.getElementById('sample'));

```

{% endtab %}
