---
title: "Custom Tooltip for columns"
component: "Grid"
description: "Learn how to Custom Tooltip for columns."
---

# Custom Tooltip for columns

To display custom Tooltip ([`EJ2 Tooltip`](../../../tooltip/getting-started)), you can render the Grid control inside the Tooltip component and set the target as `.e-rowcell`. The tooltip is displayed when hovering the grid cells.

Change the tooltip content for the grid cells by using the following code in the mouseover event.

```typescript

  public tooltipcontent(args){
     this.grid.element.addEventListener("mouseover", args => {
         if (args.target.closest("td")) {
          this.tooltip.content = args.target.innerText; // changing the tooltip content with the cell value
        }
      });
  }

```

{% tab template="grid/custom-tooltip", sourceFiles="app/App.tsx,app/datasource.tsx" %}

```typescript
import { getValue } from '@syncfusion/ej2-base';
import { Column, ColumnDirective, ColumnsDirective, GridComponent, QueryCellInfoEventArgs } from '@syncfusion/ej2-react-grids';
import { TooltipComponent } from '@syncfusion/ej2-react-popups';
import * as React from 'react';
import { data } from './datasource';

export default class App extends React.Component<{}, {}> {
  public tooltipcontent(args){
     this.grid.element.addEventListener("mouseover", args => {
         if (args.target.closest("td")) {
          this.tooltip.content = args.target.innerText;
          }
      });
  }
  public render() {
    this.tooltipcontent = this.tooltipcontent.bind(this);
    return <div><TooltipComponent ref={t => this.tooltip = t} target='.e-rowcell'>
          <GridComponent dataSource={data} height={320} load={this.tooltipcontent}  ref={g => this.grid = g}>
      <ColumnsDirective>
        <ColumnDirective field='OrderID' headerText='Order ID' width='100' textAlign="Right"/>
        <ColumnDirective field='CustomerID' headerText='Customer ID' width='100'/>
        <ColumnDirective field='EmployeeID' headerText='Employee ID' width='100' textAlign="Right"/>
        <ColumnDirective field='Freight' headerText='Freight' width='100' format="C2" textAlign="Right"/>
        <ColumnDirective field='ShipCountry' headerText='Ship Country' width='100'/>
      </ColumnsDirective>
    </GridComponent></TooltipComponent></div>
  }
};
```

{% endtab %}
