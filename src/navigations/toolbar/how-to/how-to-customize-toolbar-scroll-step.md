---
title: "How to customize toolbar scrollStep"
component: "Toolbar"
description: "This example demonstrates how to customize the scrolling distance of Essential JS 2 Toolbar control items when clicking left or right navigation icons."
---

# How to customize toolbar scrollStep

Toolbar supports to customize the scrolling distance when you click the left and right side navigation icons. we can customize `ScrollStep` property for scrolling distance. Refer to the following code example.

By using Toolbar scrollStep property, pass a required value to customize toolbar scrollStep.

{% tab template="toolbar/scrollstep", compileJsx=true %}

```typescript

import * as ReactDOM from 'react-dom';
import * as React from 'react';
import { ToolbarComponent, ItemsDirective, ItemDirective } from '@syncfusion/ej2-react-navigations';

export class ReactApp extends React.Component<{}, {}> {

  render () {
    const divMargin = { margin: '25px 0' };

    return (
      <div className='control-pane'>
        <div className='control-section tbar-control-section'>
          <div className='control toolbar-sample tbar-sample' style={divMargin}>
            <ToolbarComponent id="ej2Toolbar" width="600px" scrollStep="50">
              <ItemsDirective>
                <ItemDirective prefixIcon = 'e-cut-icon'  tooltipText = 'Cut'/>
                <ItemDirective prefixIcon = 'e-copy-icon'  tooltipText = 'Copy'/>
                <ItemDirective prefixIcon = 'e-paste-icon'  tooltipText = 'Paste'/>
                <ItemDirective type = 'Separator'/>
                <ItemDirective prefixIcon = 'e-bold-icon'  tooltipText = 'Bold'/>
                <ItemDirective prefixIcon = 'e-underline-icon'  tooltipText = 'Underline'/>
                <ItemDirective prefixIcon = 'e-italic-icon'  tooltipText = 'Italic'/>
                <ItemDirective prefixIcon = 'e-color-icon'  tooltipText = 'Color-Picker'/>
                <ItemDirective type = 'Separator'/>
                <ItemDirective prefixIcon = 'e-alignleft-icon'  tooltipText = 'Align_Left'/>
                <ItemDirective prefixIcon = 'e-alignright-icon'  tooltipText = 'Align_Right'/>
                <ItemDirective prefixIcon = 'e-aligncenter-icon'  tooltipText = 'Align_Center'/>
                <ItemDirective prefixIcon = 'e-alignjustify-icon'  tooltipText = 'Align_Justify'/>
                <ItemDirective type = 'Separator'/>
                <ItemDirective prefixIcon = 'e-bullets-icon'  tooltipText = 'Bullets'/>
                <ItemDirective prefixIcon = 'e-numbering-icon'  tooltipText = 'Numbering'/>
                <ItemDirective type = 'Separator'/>
                <ItemDirective prefixIcon = 'e-bullets-icon'  tooltipText = 'Bullets'/>
                <ItemDirective prefixIcon = 'e-numbering-icon'  tooltipText = 'Numbering'/>
                <ItemDirective type = 'Separator'/>
                <ItemDirective prefixIcon = 'e-ascending-icon'  tooltipText = 'Sort A - Z'/>
                <ItemDirective prefixIcon = 'e-descending-icon'  tooltipText = 'Sort Z - A'/>
                <ItemDirective type = 'Separator'/>
                <ItemDirective prefixIcon = 'e-indent-icon'  tooltipText = 'Text Indent'/>
                <ItemDirective prefixIcon = 'e-outdent-icon'  tooltipText = 'Text Outdent'/>
                <ItemDirective type = 'Separator'/>
                <ItemDirective prefixIcon = 'e-clear-icon'  tooltipText = 'Clear'/>
                <ItemDirective prefixIcon = 'e-reload-icon'  tooltipText = 'Reload'/>
                <ItemDirective prefixIcon = 'e-export-icon'  tooltipText = 'Export'/>
              </ItemsDirective>
            </ToolbarComponent>
          </div>
        </div>
      </div>
    );
  }
}
ReactDOM.render(<ReactApp />, document.getElementById('toolbar'));

```

{% endtab %}