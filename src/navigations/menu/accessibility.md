---
title: "Menu Accessibility"
component: "Menu"
description: "React Menu component has accessibility support to help access the features via keyboard, on-screen readers, or other assistive technology devices."
---

# Accessibility

## ARIA attributes

The web accessibility makes web content and web applications more accessible for people with disabilities. It especially helps in dynamic content change and development of advanced user interface controls with AJAX, HTML, JavaScript, and related technologies.
The menu provides a built-in compliance with `WAI-ARIA` specifications. The `WAI-ARIA` support is achieved using the attributes such as `aria-orientation`, `aria-label`, `aria-expanded`, `aria-disabled`, and `aria-haspopup` applied for menu item in
menu. It helps the people with disabilities by providing information about the widget for assistive technology in the screen readers. The menu component contains the `menubar`, `menu`, and `menuItem` roles.

| Properties | Functionality |
| ------------ | ----------------------- |
| **menubar** | This role will be specified for root menu. |
| **menu** | This role will be specified for an item that have sub menu. |
| **menuitem** | This role will be specified for an item that do not have sub menus. |
| **aria-haspopup** | Indicates the availability and type of interactive popup element. |
| **aria-expanded** | Indicates whether the subtree can be expanded or collapsed, and indicates whether its current state can be expanded or collapsed. |
| **aria-orientation** | Indicates whether the orientation is horizontal or vertical. The default orientation is horizontal. |
| **aria-label** | Indicates the menu item text. |
| **aria-disabled** | Indicates the state of menu item whether it is disabled. |

## User interaction with keyboard

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
<b>Keyboard shortcuts</b></td><td>
<b>Actions</b></td></tr>
<tr>
<td>
<kbd>Esc</kbd></td><td>
Closes the sub menu that contains focus and returns focus to the parent element.</td></tr>
<tr>
<td>
<kbd>Enter</kbd></td><td>
Opens the sub menu if focused menu item has sub menu, and places focus on its first item or activates the item and closes the sub menu.</td></tr>
<tr>
<td>
<kbd>Up</kbd></td><td>
Navigates up or to the previous menu item.</td></tr>
<tr>
<td>
<kbd>Down</kbd></td><td>
Navigates down or to the next menu item.</td></tr>
<tr>
<td>
<kbd>Left</kbd></td><td>
Closes the current sub menu and navigates to the parent menu.</td></tr>
<tr>
<td>
<kbd>Right</kbd></td><td>
Navigates and open the next sub menu.</td></tr>
<tr>
<td>
<kbd>Home</kbd></td><td>
Focuses the first item.</td></tr>
<tr>
<td>
<kbd>End</kbd></td><td>
Focuses the last item.</td></tr>
</table>

{% tab template="menu/getting-started",  sourceFiles="app/**/*.tsx,index.html", isDefaultActive=true, compileJsx=true %}

```tsx
import { enableRipple } from '@syncfusion/ej2-base';
import { MenuComponent, MenuItemModel } from '@syncfusion/ej2-react-navigations';
import * as React from 'react';
import * as ReactDom from 'react-dom';

enableRipple(true);

class App extends React.Component<{}, {}> {
    // Menu items definition
    public menuItems: MenuItemModel[] = [
        {
            items: [
                {
                    items: [
                        {
                            items: [
                                { text: 'Trimmers' },
                                { text:  'Shavers' }
                            ],
                            text: 'Personal Care'
                        },
                        {
                            items: [
                                { text: 'Shirts' },
                                { text: 'Jackets' },
                                { text: 'Track Suits' }
                            ],
                            text: 'Clothing'
                        },
                        { text: 'Footwear' }
                    ],
                    text: 'Men Fashion'
                },
                {
                    items: [
                        {
                            items: [
                                { text: 'Kurtas' },
                                { text: 'Salwars' },
                                { text: 'Sarees' }
                            ],
                            text: 'Clothing'
                        },
                        {
                            items: [
                                { text: 'Nosepins' },
                                { text:  'Anklets' }
                            ],
                            text: 'Jewellery'
                        }
                    ],
                    text: 'Women Fashion'
                }
            ],
            text: 'Fashion'
        },
        {
            items: [
                {
                    items: [
                        { text: 'Fully Automatic' },
                        { text: 'Semi Automatic' }
                    ],
                    text: 'Washing Machine'
                },
                {
                    items: [
                        { text: 'Inverter ACs' },
                        { text: 'Split ACs' }
                    ],
                    text: 'Air Conditioners'
                }
            ],
            text: 'Home & Living'
        },
        { text: 'Sports' },
        { text: 'Gaming' }
    ];
    public render() {
        return (
            <MenuComponent items={this.menuItems}/>
        );
    }
}

ReactDom.render(<App />,document.getElementById('element'));
```

{% endtab %}
