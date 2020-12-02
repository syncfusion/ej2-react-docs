---
title: "Customize the Edit Dialog"
component: "Grid"
description: "Learn how to customize the Edit Dialog."
---

# Customize the Edit Dialog

You can customize the appearance of the edit dialog in the [`actionComplete`](../../api/grid/#actioncomplete) event based on [`requestType`](../../api/grid/dialogEditEventArgs/#requesttype) as **beginEdit** or **add**.

In the below example, we have changed the dialog's header text for editing and adding records.

{% tab template="grid/customizedialog", sourceFiles="app/App.tsx,app/datasource.tsx" %}

```typescript
import { getValue } from '@syncfusion/ej2-base';
import { Dialog } from '@syncfusion/ej2-popups';
import { ColumnDirective, ColumnsDirective, EditSettingsModel, GridComponent, Inject } from '@syncfusion/ej2-react-grids';
import { DialogEditEventArgs, Edit, Toolbar, ToolbarItems } from '@syncfusion/ej2-react-grids';
import * as React from 'react';
import { data } from './datasource';

export default class App extends React.Component<{}, {}> {
  public editOptions: EditSettingsModel = { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Dialog' };
  public toolbarOptions: ToolbarItems[] = ['Add', 'Edit', 'Delete'];

  public actionComplete(args: DialogEditEventArgs): void {
    if ((args.requestType === 'beginEdit' || args.requestType === 'add')) {
      const dialog: Dialog = args.dialog as Dialog;
      dialog.height = 400;
      // change the header of the dialog
      dialog.header = args.requestType === 'beginEdit' ?
        'Record of ' +  getValue('CustomerID', args.rowData) : 'New Customer';
    }
  }

  public render() {
    this.actionComplete = this.actionComplete.bind(this);
    return <GridComponent dataSource={data} actionComplete={this.actionComplete}
      editSettings={this.editOptions} toolbar={this.toolbarOptions} height={265}>
      <ColumnsDirective>
        <ColumnDirective field='OrderID' headerText='Order ID' width='100' textAlign="Right" isPrimaryKey={true}/>
        <ColumnDirective field='CustomerID' headerText='Customer ID' width='120'/>
        <ColumnDirective field='ShipCountry' headerText='Ship Country' width='150'/>
      </ColumnsDirective>
      <Inject services={[Edit, Toolbar]} />
    </GridComponent>
  }
};
```

{% endtab %}
