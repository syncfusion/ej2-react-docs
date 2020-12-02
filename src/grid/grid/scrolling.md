---
title: "Scrolling"
component: "Grid"
description: "Learn how to set width and height for DataGrid content, display a scrollbar, freeze rows and columns, and make the DataGrid responsive with a parent container."
---

# Scrolling

 The scrollbar will be displayed in the grid when content exceeds the element [`width`](../api/grid/#width) or [`height`](../api/grid/#height).
 The vertical and horizontal scrollbars will be displayed based on the following criteria:

* The vertical scrollbar appears when the total height of rows present in the grid exceeds its element height.
* The horizontal scrollbar appears when the sum of columns width exceeds the grid element width.
* The [`height`](../api/grid/#height) and
[`width`](../api/grid/#width) are used to set the grid height and width, respectively.

> The default value for [`height`](../api/grid/#height) and [`width`](../api/grid/#width) is **auto**.

## Set width and height

To specify the [`width`](../api/grid/#width) and [`height`](../api/grid/#height)
of scroller in pixel, set the pixel value as number.

{% tab template="grid/scrolling", sourceFiles="app/App.tsx,app/datasource.tsx" %}

```typescript
import { ColumnDirective, ColumnsDirective, GridComponent } from '@syncfusion/ej2-react-grids';
import * as React from 'react';
import { data } from './datasource';

export default class App extends React.Component<{}, {}>{
  public render() {
    return <GridComponent dataSource={data} height={315} width={400}>
            <ColumnsDirective>
             <ColumnDirective field='OrderID' width='120' textAlign='Right'/>
             <ColumnDirective field='CustomerID' width='150'/>
             <ColumnDirective field='EmployeeID' width='120' textAlign='Right'/>
             <ColumnDirective field='ShipCity' width='150'/>
             <ColumnDirective field='ShipCountry' width='150'/>
             <ColumnDirective field='ShipName' width='150'/>
            </ColumnsDirective>
           </GridComponent>
  }
};
```

{% endtab %}

## Responsive with parent container

Specify the [`width`](../api/grid/#width) and [`height`](../api/grid/#height) as **100%** to make the grid element fill its parent container.
Setting the [`height`](../api/grid/#height) to **100%** requires the grid parent element to have explicit height.

{% tab template="grid/scrolling", sourceFiles="app/App.tsx,app/datasource.tsx" %}

```typescript
import { ColumnDirective, ColumnsDirective, GridComponent } from '@syncfusion/ej2-react-grids';
import * as React from 'react';
import { data } from './datasource';

export default class App extends React.Component<{}, {}>{
  public inlineStyle: object = { width: '376px'};
  public render() {
    return (<div style={this.inlineStyle}>
            <GridComponent dataSource={data} height='100%' width='100%'>
              <ColumnsDirective>
                <ColumnDirective field='OrderID' width='120' textAlign='Right'/>
                <ColumnDirective field='CustomerID' width='150'/>
                <ColumnDirective field='EmployeeID' width='120' textAlign='Right'/>
                <ColumnDirective field='ShipCity' width='150'/>
                <ColumnDirective field='ShipCountry' width='150'/>
                <ColumnDirective field='ShipName' width='150'/>
              </ColumnsDirective>
           </GridComponent>
    </div>)
  }
};
```

{% endtab %}

## Scroll To Selected Row

You can scroll the grid content to the selected row position by using the [`rowSelected`](../api/grid/#rowselected) event.

{% tab template="grid/scrolling", sourceFiles="app/App.tsx,app/datasource.tsx" %}

```typescript
import { ColumnDirective, ColumnsDirective, Grid, GridComponent, RowSelectEventArgs } from '@syncfusion/ej2-react-grids';
import { NumericTextBox, NumericTextBoxComponent } from '@syncfusion/ej2-react-inputs';
import * as React from 'react';
import { data } from './datasource';

export default class App extends React.Component<{}, {}>{
  public grid: Grid | null;
  public numeric: NumericTextBox | null;
  public onChange(){
    if (this.grid && this.numeric) {
      this.grid.selectionModule.selectRow(parseInt(this.numeric.getText(), 10));
    }
  }
  public rowSelected(args: RowSelectEventArgs) {
    if (this.grid) {
      const rowHeight: number =
        this.grid.getRows()[this.grid.getSelectedRowIndexes()[0]].scrollHeight;
      this.grid.getContent().children[0].scrollTop =
        rowHeight * this.grid.getSelectedRowIndexes()[0];
    }
  }
  public render() {
      this.rowSelected = this.rowSelected.bind(this);
      this.onChange = this.onChange.bind(this);
      return (<div>
            <NumericTextBoxComponent format={'N'} placeholder='Enter index to select a row'
              width={200} showSpinButton={false} change={this.onChange}
              ref={n=> this.numeric = n}/>
            <GridComponent dataSource={data} height="275" width="100%"
              rowSelected={this.rowSelected} ref={g => this.grid = g}>
              <ColumnsDirective>
               <ColumnDirective field='OrderID' width='120' textAlign="Right"/>
               <ColumnDirective field='CustomerID' width='150'/>
               <ColumnDirective field='EmployeeID' width='120' textAlign="Right"/>
               <ColumnDirective field='ShipCity' width='150'/>
              </ColumnsDirective>
             </GridComponent></div>)
  }
};
```

{% endtab %}

## Frozen rows and columns

Frozen rows and columns provides an option to make rows and columns always visible in the top and left side of the grid while scrolling.

To use frozen rows and columns support, inject the **Freeze** module in the Grid.

In this demo, the [`frozenColumns`](../api/grid/#frozencolumns) is set as **'2'** and the [`frozenRows`](../api/grid/#frozenrows)
is set as **'3'**. Hence, the left two columns and top three rows are frozen.

{% tab template="grid/scrolling", sourceFiles="app/App.tsx,app/datasource.tsx" %}

```typescript
import { ColumnDirective, ColumnsDirective, Freeze, GridComponent, Inject } from '@syncfusion/ej2-react-grids';
import * as React from 'react';
import { data } from './datasource';

export default class App extends React.Component<{}, {}>{
  public render() {
    return (<div>
          <GridComponent dataSource={data} height="315" frozenRows={3} frozenColumns={2}
            allowSelection={false} enableHover={false}>
            <ColumnsDirective>
             <ColumnDirective field='OrderID' width='120' textAlign='Right'/>
             <ColumnDirective field='CustomerID' width='150'/>
             <ColumnDirective field='OrderDate' width='130' format='yMd' textAlign='Right'/>
             <ColumnDirective field='EmployeeID' width='120' textAlign="Right"/>
             <ColumnDirective field='ShipName' width='150'/>
             <ColumnDirective field='ShipAddress' width='170'/>
             <ColumnDirective field='ShipCity' width='150'/>
             <ColumnDirective field='ShipCountry' width='150'/>
             <ColumnDirective field='ShipRegion' width='150'/>
             <ColumnDirective field='ShipPostalCode' width='150'/>
             <ColumnDirective field='Freight' width='120'/>
            </ColumnsDirective>
            <Inject services={[Freeze]} />
           </GridComponent></div>)
  }
};
```

{% endtab %}

> Frozen rows and columns should not be set outside the grid view port.
> Frozen Grid will support row and column virtualization feature, which helps to improve the Grid performance while loading a large dataset.

### Limitations

The following features are not supported in frozen rows and columns:

* Grouping
* Row Template
* Detail Template
* Hierarchy Grid