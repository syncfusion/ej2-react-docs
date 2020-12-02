---
title: "Enable editing in single click"
component: "Grid"
description: "Learn how to enable single click editing in the Essential JS 2 DataGrid control."
---

# Enable editing in single click

## Normal Editing

You can make a row editable on a single click with **Normal** mode of editing in Grid, by using the [`startEdit`](../../api/grid/#startedit) and [`endEdit`](../../api/grid/#endedit) methods.

Bind the **mousedown** event for Grid and in the event handler call the [`startEdit`](../../api/grid/#startedit) and [`endEdit`](../../api/grid/#endedit), based on the clicked target element.

{% tab template="grid/editing", sourceFiles="app/App.tsx,app/datasource.tsx" %}

```typescript
import { ColumnDirective, ColumnsDirective, GridComponent, Inject, Edit, Page, Toolbar, ToolbarItems, EditSettingsModel } from '@syncfusion/ej2-react-grids';
import { MouseEventArgs } from '@syncfusion/ej2-base';
import * as React from 'react';
import { data } from './datasource';

export default class App extends React.Component<{}, {}> {
    public editSettings: EditSettingsModel = { allowEditing: true, allowAdding:   true, allowDeleting: true, mode: 'Normal' };
    public toolbarOptions: ToolbarItems[] = ['Add', 'Edit', 'Delete', 'Update', 'Cancel'];
    public load(): void {
        let instance = this.gridInstance;
        instance.element.addEventListener('mousedown', function (e) {
            if ((e.target as HTMLElement).classList.contains("e-rowcell")) {
                if (instance.isEdit)
                    instance.endEdit();
                let index: number = parseInt((e.target as HTMLElement).getAttribute("Index"));
                instance.selectRow(index);
                instance.startEdit();
            };
        });
    }
    public render() {
      return <GridComponent dataSource={data} ref={grid => this.gridInstance = grid} toolbar={this.toolbarOptions} allowPaging={true} editSettings={this.editSettings} load={this.load.bind(this)}>
              <ColumnsDirective>
                <ColumnDirective field='OrderID' headerText='Order ID' textAlign='Right' width='100' isPrimaryKey={true}></ColumnDirective>
                <ColumnDirective field='CustomerID' headerText='Customer ID' width='120'></ColumnDirective>
                <ColumnDirective field='Freight' headerText='Freight' textAlign='Right'  width='120' format='C2' ></ColumnDirective>
                <ColumnDirective field='ShipCountry' headerText='Ship Country' width='150'></ColumnDirective>
              </ColumnsDirective>
              <Inject services={[Page, Toolbar, Edit]}/>
            </GridComponent>
    }
}
```

{% endtab %}

## Batch Editing

You can make a cell editable on a single click with **Batch** mode of editing in Grid, by using the [`editCell`](../../api/grid/edit/#editcell) method.

Bind the **mousedown** event for Grid and in the event handler call the [`editCell`](../../api/grid/edit/#editcell) method, based on the clicked target element.

{% tab template="grid/editing", sourceFiles="app/App.tsx,app/datasource.tsx" %}

```typescript
import { ColumnDirective, ColumnsDirective, GridComponent, Inject, Edit, Page, Toolbar, ToolbarItems, EditSettingsModel } from '@syncfusion/ej2-react-grids';
import * as React from 'react';
import { data } from './datasource';

export default class App extends React.Component<{}, {}> {
    public editSettings: EditSettingsModel = { allowEditing: true, allowAdding:   true, allowDeleting: true, mode: 'Batch' };
    public toolbarOptions: ToolbarItems[] = ['Add', 'Edit', 'Delete', 'Update', 'Cancel'];
    public load(): void {
        let instance = this.gridInstance;
        instance.element.addEventListener('mousedown', (e: MouseEventArgs) => {
        if ((e.target as HTMLElement).classList.contains("e-rowcell")) {
            let index: number = parseInt((e.target as HTMLElement).parentElement.getAttribute("aria-rowindex"));
            let colindex: number = parseInt((e.target as HTMLElement).getAttribute("aria-colindex"));
            let field: string = instance.getColumns()[colindex].field;
            instance.editModule.editCell(index, field);
        };
        });
    }
    public render() {
      return <GridComponent dataSource={data} ref={grid => this.gridInstance = grid} toolbar={this.toolbarOptions} allowPaging={true} editSettings={this.editSettings} load={this.load.bind(this)}>
              <ColumnsDirective>
                <ColumnDirective field='OrderID' headerText='Order ID' textAlign='Right' width='100' isPrimaryKey={true}></ColumnDirective>
                <ColumnDirective field='CustomerID' headerText='Customer ID' width='120'></ColumnDirective>
                <ColumnDirective field='Freight' headerText='Freight' textAlign='Right'  width='120' format='C2' ></ColumnDirective>
                <ColumnDirective field='ShipCountry' headerText='Ship Country' width='150'></ColumnDirective>
              </ColumnsDirective>
              <Inject services={[Page, Toolbar, Edit]}/>
            </GridComponent>
    }
}
```

{% endtab %}