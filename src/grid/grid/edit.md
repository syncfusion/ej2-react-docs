---
title: "Editing"
component: "Grid"
description: "Learn how to perform CRUD operations in various edit modes, use different cell editors, and persist data on the server side in the Essential JS 2 DataGrid control."
---

# Editing

The Grid component has options to dynamically insert, delete and update records.
Editing feature requires a primary key column for CRUD operations.
To define primary key, set [`columns.isPrimaryKey`](../api/grid/column/#isprimarykey) to **true** in particular column.

You can start the edit action either by double clicking the particular row or by selecting the required row and click on **Edit** button in the toolbar. Similarly, you can add a new record to grid either by clicking on **Add** button in the toolbar or on an external button which is bound to invoke the [`addRecord`](../api/grid/edit/#addrecord) method of the grid, **Save** and **Cancel** while in edit mode is possible using respective toolbar icon in grid.

Deletion of the record is possible by selecting the required row and click on **Delete** button in toolbar.

To use CRUD, inject the [`Edit`](../api/grid/edit/) module in grid.

{% tab template="grid/editing", sourceFiles="app/App.tsx,app/datasource.tsx" %}

```typescript
import { ColumnDirective, ColumnsDirective, GridComponent } from '@syncfusion/ej2-react-grids';
import { Edit, EditSettingsModel, Inject } from '@syncfusion/ej2-react-grids';
import * as React from 'react';
import { data } from './datasource';

export default class App extends React.Component<{}, {}> {
  public editOptions: EditSettingsModel = { allowEditing: true, allowAdding: true, allowDeleting: true };

  public render() {
    return <GridComponent dataSource={data} editSettings={this.editOptions} height={315}>
        <ColumnsDirective>
            <ColumnDirective field='OrderID' headerText='Order ID' width='100' textAlign="Right" isPrimaryKey={true}/>
            <ColumnDirective field='CustomerID' headerText='Customer ID' width='120'/>
            <ColumnDirective field='Freight' headerText='Freight' width='120' format="C2" textAlign="Right"/>
            <ColumnDirective field='ShipCountry' headerText='Ship Country' width='150'/>
        </ColumnsDirective>
        <Inject services={[Edit]} />
    </GridComponent>
  }
}
```

{% endtab %}

> * If [`columns.isIdentity`](../api/grid/column/#isidentity) is enabled, then it will be considered as read-only column when editing and adding a record.
> * You can disable editing for a particular column, by specifying
[`columns.allowEditing`](../api/grid/column/#allowediting) to **false**.

## Toolbar with edit option

The grid toolbar has the [built-in items](./tool-bar#built-in-toolbar-items) to execute Editing actions.
You can define this by using the [`toolbar`](../api/grid/#toolbar) property.

{% tab template="grid/editing", sourceFiles="app/App.tsx,app/datasource.tsx" %}

```typescript
import { ColumnDirective, ColumnsDirective, GridComponent } from '@syncfusion/ej2-react-grids';
import { Edit, EditSettingsModel, Inject, Toolbar, ToolbarItems } from '@syncfusion/ej2-react-grids';
import * as React from 'react';
import { data } from './datasource';

export default class App extends React.Component<{}, {}> {
  public editOptions: EditSettingsModel = { allowEditing: true, allowAdding: true, allowDeleting: true };
  public toolbarOptions: ToolbarItems[] = ['Add', 'Edit', 'Delete', 'Update', 'Cancel'];

  public render() {
    return <GridComponent dataSource={data} editSettings={this.editOptions} toolbar={this.toolbarOptions} height={265}>
        <ColumnsDirective>
            <ColumnDirective field='OrderID' headerText='Order ID' width='100' textAlign="Right" isPrimaryKey={true}/>
            <ColumnDirective field='CustomerID' headerText='Customer ID' width='120'/>
            <ColumnDirective field='Freight' headerText='Freight' width='120' format="C2" textAlign="Right"/>
            <ColumnDirective field='ShipCountry' headerText='Ship Country' width='150'/>
        </ColumnsDirective>
        <Inject services={[Edit, Toolbar]} />
    </GridComponent>
  }
}
```

{% endtab %}

## Cell edit type and its params

The [`columns.editType`](../api/grid/column/#edittype) is used to define the editor component for any particular column.
You can set the [`columns.editType`](../api/grid/column/#edittype) based on data type of the column.

* [`NumericTextBox`](../numerictextbox) component for integers, double, and decimal data types.

* [`TextBox`](../textbox) component for string data type.

* [`DropDownList`](../drop-down-list) component to show all unique values related to that field.

* [`CheckBox`](../check-box) component for boolean data type.

* [`DatePicker`](../datepicker) component for date data type.

* [`DateTimePicker`](../datetimepicker) component for date time data type.

Also, you can customize the behavior of the editor component through the [`columns.edit.params`](../api/grid/column/#edit).

The following table describes editor component and their example edit params of the column.

Component |Example
-----|-----
[`NumericTextBox`](../numerictextbox) | params: { decimals: 2, value: 5 }
[`DropDownList`](../drop-down-list) | params: { value: 'Germany' }
[`Checkbox`](../check-box) | params: { checked: true}
[`DatePicker`](../datepicker) | params: { format:'dd.MM.yyyy' }
[`DateTimePicker`](../datetimepicker) | params: { value: new Date() }

{% tab template="grid/editing", sourceFiles="app/App.tsx,app/datasource.tsx" %}

```typescript
import { ColumnDirective, ColumnsDirective, GridComponent, IEditCell } from '@syncfusion/ej2-react-grids';
import { Edit, EditSettingsModel, Inject, Toolbar, ToolbarItems } from '@syncfusion/ej2-react-grids';
import * as React from 'react';
import { data } from './datasource';

export default class App extends React.Component<{}, {}> {
  public editOptions: EditSettingsModel = { allowEditing: true, allowAdding: true, allowDeleting: true };
  public toolbarOptions: ToolbarItems[] = ['Add', 'Edit', 'Delete', 'Update', 'Cancel'];
  public numericParams: IEditCell = { params: { decimals: 2 } };
  public ddParams: IEditCell = { params: { value: 'Germany' } };
  public verifiedParams: any = { params: { checked: true} };

  public render() {
    return <GridComponent dataSource={data} editSettings={this.editOptions} toolbar={this.toolbarOptions} height={265}>
        <ColumnsDirective>
            <ColumnDirective field='OrderID' headerText='Order ID' width='100' textAlign="Right" isPrimaryKey={true}/>
            <ColumnDirective field='CustomerID' headerText='Customer ID' width='120'/>
            <ColumnDirective field='Freight' headerText='Freight' width='120' format="C2" editType= 'numericedit' edit={this.numericParams} textAlign="Right"/>
            <ColumnDirective field='ShipCountry' headerText='Ship Country' editType= 'dropdownedit' edit={this.ddParams} width='150'/>
            <ColumnDirective field='Verified' headerText='Verified' displayAsCheckBox={true}editType='booleanedit' edit={this.verifiedParams} width='150'/>
        </ColumnsDirective>
        <Inject services={[Edit, Toolbar]} />
    </GridComponent>
  }
}
```

{% endtab %}

> If edit type is not defined in the column, then it will be considered as the **stringedit** type (Textbox component) .

## Cell Edit Template

The cell edit template is used to add a custom component for a particular column by invoking the following functions:

* **create** - It is used to create the element at time of initialization.

* **write** - It is used to create custom component or assign default value at time of editing.

* **read** - It is used to read the value from component at time of save.

* **destroy** - It is used to destroy the component.

{% tab template="grid/editing", sourceFiles="app/App.tsx,app/datasource.tsx" %}

```typescript
import { DatePicker } from '@syncfusion/ej2-calendars';
import { Column, ColumnDirective, ColumnsDirective, GridComponent, IEditCell } from '@syncfusion/ej2-react-grids';
import { Edit, EditSettingsModel, Inject, Toolbar, ToolbarItems } from '@syncfusion/ej2-react-grids';
import * as React from 'react';
import { data } from './datasource';

export default class App extends React.Component<{}, {}> {
  public editOptions: EditSettingsModel = { allowEditing: true, allowAdding: true, allowDeleting: true };
  public toolbarOptions: ToolbarItems[] = ['Add', 'Edit', 'Delete', 'Update', 'Cancel'];
  public elem : HTMLElement;
  public datePickerObj: DatePicker;
  public datepickerTemp : IEditCell = {
    create:()=>{
        this.elem = document.createElement('input');
        return this.elem;
    },
    destroy:()=>{
        this.datePickerObj.destroy();
    },
    read:()=>{
        return this.datePickerObj.value;
    },
    write:(args:{rowData: object, column: Column})=>{
        this.datePickerObj = new DatePicker({
          floatLabelType: 'Never',
          value: new Date(args.rowData[args.column.field])
        });
      this.datePickerObj.appendTo(this.elem);
    }
  };

  public render() {
    return <GridComponent dataSource={data} editSettings={this.editOptions} toolbar={this.toolbarOptions} height={265}>
      <ColumnsDirective>
        <ColumnDirective field='OrderID' headerText='Order ID' width='100' textAlign="Right" isPrimaryKey={true}/>
        <ColumnDirective field='CustomerID' headerText='Customer ID' width='120'/>
        <ColumnDirective field='Freight' headerText='Freight' width='120' format="C2" editType= 'numericedit' textAlign="Right"/>
        <ColumnDirective field='OrderDate' headerText='Order Date' type= 'date' format= 'yMd' edit={this.datepickerTemp}  width='150'/>
      </ColumnsDirective>
      <Inject services={[Edit, Toolbar]} />
    </GridComponent>
  }
}
```

{% endtab %}

### Using template

The cell editor for a particular column can be specified using a React Component. The [`column.editTemplate`](../api/grid/column/#edittemplate) property used to define the corresponding column editor.

{% tab template="grid/editing", sourceFiles="app/App.tsx,app/datasource.tsx" %}

```typescript
import { getValue } from '@syncfusion/ej2-base';
import { DatePickerComponent } from '@syncfusion/ej2-react-calendars';
import { ColumnDirective, ColumnsDirective, GridComponent } from '@syncfusion/ej2-react-grids';
import { Edit, EditSettingsModel, Inject, Toolbar, ToolbarItems } from '@syncfusion/ej2-react-grids';
import * as React from 'react';
import { data } from './datasource';

export default class App extends React.Component<{}, {}> {
  public editOptions: EditSettingsModel = { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Normal' };
  public toolbarOptions: ToolbarItems[] = ['Add', 'Edit', 'Delete', 'Update', 'Cancel'];

  public editTemplate(args: object) {
      return (<DatePickerComponent value={getValue('OrderDate', args)} id="OrderDate" placeholder="Order Date" floatLabelType='Never'/>)
  }

  public render() {
    return <GridComponent dataSource={data} editSettings={this.editOptions} toolbar={this.toolbarOptions} height={265}>
      <ColumnsDirective>
          <ColumnDirective field='OrderID' headerText='Order ID' width='100' textAlign="Right" isPrimaryKey={true}/>
          <ColumnDirective field='CustomerID' headerText='Customer ID' width='120'/>
          <ColumnDirective field='Freight' headerText='Freight' width='120' format="C2" editType= 'numericedit' textAlign="Right"/>
          <ColumnDirective field='OrderDate' headerText='OrderDate' type='date' format= 'yMd' width='150' editTemplate={this.editTemplate}/>
      </ColumnsDirective>
      <Inject services={[Edit, Toolbar]} />
    </GridComponent>
  }
};
```

{% endtab %}

## Edit Modes

Grid supports the following types of edit modes, they are:

* Normal
* Dialog
* Batch

### Normal

In Normal edit mode, when you start editing the currently selected record is changed to edit state.
You can change the cell values and save edited data to the datasource.
To enable Normal edit, set the [`editSettings.mode`](../api/grid/editSettings/#mode) as **Normal**.

{% tab template="grid/editing", sourceFiles="app/App.tsx,app/datasource.tsx" %}

```typescript
import { ColumnDirective, ColumnsDirective, GridComponent } from '@syncfusion/ej2-react-grids';
import { Edit, EditSettingsModel, Inject, Toolbar, ToolbarItems } from '@syncfusion/ej2-react-grids';
import * as React from 'react';
import { data } from './datasource';

export default class App extends React.Component<{}, {}> {
  public editOptions: EditSettingsModel = { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Normal' };
  public toolbarOptions: ToolbarItems[] = ['Add', 'Edit', 'Delete', 'Update', 'Cancel'];

  public render() {
    return <GridComponent dataSource={data} editSettings={this.editOptions} toolbar={this.toolbarOptions} height={265}>
      <ColumnsDirective>
          <ColumnDirective field='OrderID' headerText='Order ID' width='100' textAlign="Right" isPrimaryKey={true}/>
          <ColumnDirective field='CustomerID' headerText='Customer ID' width='120'/>
          <ColumnDirective field='Freight' headerText='Freight' width='120' format="C2" editType= 'numericedit' textAlign="Right"/>
          <ColumnDirective field='ShipCountry' headerText='Ship Country' editType= 'dropdownedit' width='150'/>
      </ColumnsDirective>
      <Inject services={[Edit, Toolbar]} />
    </GridComponent>
  }
};
```

{% endtab %}

> Normal edit mode is default mode of editing.

### Automatically update the column based on another column edited value

You can update the column value based on another column edited value by using the Cell Edit Template feature.

In the below demo, we have update the `TotalCost` column value based on the `UnitPrice` and `UnitInStock` column value while editing.

{% tab template="grid/editing", sourceFiles="app/App.tsx,app/datasource.tsx" %}

```typescript
import { ColumnDirective, ColumnsDirective, EditSettingsModel, GridComponent } from '@syncfusion/ej2-react-grids';
import { Edit, IEditCell, Inject, Toolbar, ToolbarItems } from '@syncfusion/ej2-react-grids';
import { NumericTextBox } from '@syncfusion/ej2-inputs';
import * as React from 'react';
import { productData } from './datasource';

export default class App extends React.Component<{}, {}> {
  public editOptions: EditSettingsModel = { allowEditing: true, allowAdding: true, allowDeleting: true };
  public toolbarOptions: ToolbarItems[] = ['Add', 'Edit', 'Delete', 'Update', 'Cancel'];
  public priceParams : IEditCell = {
    create: () => {
      this.priceElem = document.createElement('input');
      return this.priceElem;
    },
    read: () => {
      return this.priceObj.value;
    },
    destroy: () => {
      this.priceObj.destroy();
    },
    write: args => {
      this.priceObj = new NumericTextBox({
        value: args.rowData[args.column.field],
        change: function(args) {
          var formEle = this.gridInstance.element.querySelector('form').ej2_instances[0];
          var totalCostFieldEle = formEle.getInputElement('TotalCost');
          totalCostFieldEle.value = this.priceObj.value * this.stockObj.value;
        }.bind(this)
      });
      this.priceObj.appendTo(this.priceElem);
    }
  };
  public stockParams : object = {
    create: () => {
      this.stockElem = document.createElement('input');
      return this.stockElem;
    },
    read: () => {
      return this.stockObj.value;
    },
    destroy: () => {
      this.stockObj.destroy();
    },
    write: args => {
      this.stockObj = new NumericTextBox({
        value: args.rowData[args.column.field],
        change: function(args) {
          var formEle = this.gridInstance.element.querySelector('form').ej2_instances[0];
          var totalCostFieldEle = formEle.getInputElement('TotalCost');
          totalCostFieldEle.value = this.priceObj.value * this.stockObj.value;
        }.bind(this)
      });
      this.stockObj.appendTo(this.stockElem);
    }
  };

  public priceElem: HTMLElement;
  public priceObj: NumericTextBox;

  public stockElem: HTMLElement;
  public stockObj: NumericTextBox;

  public render() {
    return <GridComponent dataSource={productData} ref={grid => this.gridInstance = grid} editSettings={this.editOptions}
        toolbar={this.toolbarOptions} height={273}>
        <ColumnsDirective>
          <ColumnDirective field="ProductID" headerText="Product ID" textAlign="Right" isPrimaryKey={true} width="100"/>
          <ColumnDirective field="ProductName" headerText="Product Name" width="120"/>
          <ColumnDirective field="UnitPrice" headerText="Unit Price" editType="numericedit"  edit={this.priceParams} width="150" format="C2" textAlign="Right"/>
          <ColumnDirective field="UnitsInStock" headerText="Units In Stock" editType="numericedit"  edit={this.stockParams} width="150" textAlign="Right"/>
          <ColumnDirective field="TotalCost" headerText="Total Cost" width="150" allowEditing={false} format="C2" textAlign="Right"/>
        </ColumnsDirective>
        <Inject services={[Edit, Toolbar]} />
    </GridComponent>
  }
};
```

{% endtab %}

#### Cancel edit based on condition

You can prevent the CRUD operations of the Grid by using condition in the [`actionBegin`](../api/grid/#actionbegin) event with requestType as `beginEdit` for editing, `add` for adding and `delete` for deleting actions.

In the below demo, we prevent the CRUD operation based on the `Role` column value. If the Role Column is ‘employee’, we are unable to edit/delete that row.

{% tab template="grid/editing", sourceFiles="app/App.tsx,app/datasource.tsx" %}

```typescript
import { ColumnDirective, ColumnsDirective, GridComponent } from '@syncfusion/ej2-react-grids';
import { Edit, EditSettingsModel, Inject, Toolbar, ToolbarItems } from '@syncfusion/ej2-react-grids';
import * as React from 'react';
import { data } from './datasource';

export default class App extends React.Component<{}, {}> {
  public editOptions: EditSettingsModel = { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Normal' };
  public toolbarOptions: ToolbarItems[] = ['Add', 'Edit', 'Delete', 'Update', 'Cancel'];
  public isAddable: boolean = true;
  public actionBegin (args) {
      if (args.requestType == 'beginEdit') {
        if (args.rowData['Role'].toLowerCase() == 'employee') {
           args.cancel = true;
        }
      }
      if (args.requestType == 'delete') {
        if (args.data[0]['Role'].toLowerCase() == 'employee') {
          args.cancel = true;
        }
      }
      if (args.requestType == 'add') {
        if (!this.isAddable) {
          args.cancel = true;
        }
      }
  }
  public btnClick = (args) => {
    args.target.innerText == 'Grid is Addable' ? (args.target.innerText = 'Grid is Not Addable') : (args.target.innerText = 'Grid is Addable');
    this.isAddable = !this.isAddable;
  }

  public render() {
    this.actionBegin = this.actionBegin.bind(this);
    this.btnClick = this.btnClick.bind(this);
    return (<div>
    <button onClick={this.btnClick}>Grid is Addable</button>
    <GridComponent dataSource={data} editSettings={this.editOptions} toolbar={this.toolbarOptions} actionBegin= {this.actionBegin} height={240}>
      <ColumnsDirective>
          <ColumnDirective field='OrderID' headerText='Order ID' width='100' textAlign="Right" isPrimaryKey={true}/>
          <ColumnDirective field='Role' headerText='Role' width='120'/>
          <ColumnDirective field='Freight' headerText='Freight' width='120' format="C2" editType= 'numericedit' textAlign="Right"/>
          <ColumnDirective field='ShipCountry' headerText='Ship Country' editType= 'dropdownedit' width='150'/>
      </ColumnsDirective>
      <Inject services={[Edit, Toolbar]} />
    </GridComponent>
    </div>)
  }
};
```

{% endtab %}

### Dialog

In Dialog edit mode, when you start editing the currently selected row data will be shown on a dialog.
You can change the cell values and save edited data to the data source.
To enable Dialog edit, set the [`editSettings.mode`](../api/grid/editSettings/#mode) as **Dialog**.

{% tab template="grid/editing", sourceFiles="app/App.tsx,app/datasource.tsx" %}

```typescript
import { ColumnDirective, ColumnsDirective, GridComponent } from '@syncfusion/ej2-react-grids';
import { Edit, EditSettingsModel, Inject, Toolbar, ToolbarItems } from '@syncfusion/ej2-react-grids';
import * as React from 'react';
import { data } from './datasource';

export default class App extends React.Component<{}, {}> {
  public editOptions: EditSettingsModel = { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Dialog' };
  public toolbarOptions: ToolbarItems[] = ['Add', 'Edit', 'Delete', 'Update', 'Cancel'];

  public render() {
    return <GridComponent dataSource={data} editSettings={this.editOptions} toolbar={this.toolbarOptions} height={265}>
      <ColumnsDirective>
          <ColumnDirective field='OrderID' headerText='Order ID' width='100' textAlign="Right" isPrimaryKey={true}/>
          <ColumnDirective field='CustomerID' headerText='Customer ID' width='120'/>
          <ColumnDirective field='Freight' headerText='Freight' width='120' format="C2" editType= 'numericedit' textAlign="Right"/>
          <ColumnDirective field='ShipCountry' headerText='Ship Country' editType= 'dropdownedit' width='150'/>
      </ColumnsDirective>
      <Inject services={[Edit, Toolbar]} />
    </GridComponent>
  }
};
```

{% endtab %}

### Batch

In Batch edit mode, when you double-click on the grid cell, then the target cell changed to edit state.
You can bulk save (added, changed and deleted data in the single request) to data source by click on the toolbar's **Update** button or by externally invoking the [`batchSave`](../api/grid/edit/#batchsave) method.
To enable Batch edit, set the [`editSettings.mode`](../api/grid/editSettings/#mode) as **Batch**.

{% tab template="grid/editing", sourceFiles="app/App.tsx,app/datasource.tsx" %}

```typescript
import { ColumnDirective, ColumnsDirective, GridComponent } from '@syncfusion/ej2-react-grids';
import { Edit, EditSettingsModel, Inject, Toolbar, ToolbarItems } from '@syncfusion/ej2-react-grids';
import * as React from 'react';
import { data } from './datasource';

export default class App extends React.Component<{}, {}> {
  public editOptions: EditSettingsModel = { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Batch' };
  public toolbarOptions: ToolbarItems[] = ['Add', 'Edit', 'Delete', 'Update', 'Cancel'];

  public render() {
    return <GridComponent dataSource={data} editSettings={this.editOptions} toolbar={this.toolbarOptions} height={265}>
      <ColumnsDirective>
          <ColumnDirective field='OrderID' headerText='Order ID' width='100' textAlign="Right" isPrimaryKey={true}/>
          <ColumnDirective field='CustomerID' headerText='Customer ID' width='120'/>
          <ColumnDirective field='Freight' headerText='Freight' width='120' format="C2" editType= 'numericedit' textAlign="Right"/>
          <ColumnDirective field='ShipCountry' headerText='Ship Country' editType= 'dropdownedit' width='150'/>
      </ColumnsDirective>
      <Inject services={[Edit, Toolbar]} />
    </GridComponent>
  }
};
```

{% endtab %}

### Automatically update the column based on another column edited value in Batch mode

You can update the column value based on another column edited value in Batch mode by using the Cell Edit Template feature.

In the below demo, we have update the `TotalCost` column value based on the `UnitPrice` and `UnitInStock` column value while editing.

{% tab template="grid/editing", sourceFiles="app/App.tsx,app/datasource.tsx" %}

```typescript
import { ColumnDirective, ColumnsDirective, EditSettingsModel, GridComponent } from '@syncfusion/ej2-react-grids';
import { Edit, IEditCell, Inject, Toolbar, ToolbarItems } from '@syncfusion/ej2-react-grids';
import { NumericTextBox } from '@syncfusion/ej2-inputs';
import * as React from 'react';
import { productData } from './datasource';

export default class App extends React.Component<{}, {}> {
  public editOptions: EditSettingsModel = { allowEditing: true, allowAdding: true, allowDeleting: true,mode: 'Batch'  };
  public toolbarOptions: ToolbarItems[] = ['Add', 'Delete', 'Update', 'Cancel'];
  public priceParams : IEditCell = {
    create: () => {
      this.priceElem = document.createElement('input');
      return this.priceElem;
    },
    read: () => {
      return this.priceObj.value;
    },
    destroy: () => {
      this.priceObj.destroy();
    },
    write: args => {
      var rowData = args.rowData;
      var rowIndex = this.gridInstance.getRowInfo(args.row).rowIndex;
      this.priceObj = new NumericTextBox({
        value: args.rowData[args.column.field],
        change: function(args) {
            var totalCostValue = args.value * rowData['UnitsInStock'];
            this.gridInstance.updateCell(rowIndex, 'TotalCost', totalCostValue);
        }.bind(this)
      });
      this.priceObj.appendTo(this.priceElem);
    }
  };
  public stockParams : object = {
    create: () => {
      this.stockElem = document.createElement('input');
      return this.stockElem;
    },
    read: () => {
      return this.stockObj.value;
    },
    destroy: () => {
      this.stockObj.destroy();
    },
    write: args => {
      var rowData = args.rowData;
      var rowIndex = this.gridInstance.getRowInfo(args.row).rowIndex;
      this.stockObj = new NumericTextBox({
        value: args.rowData[args.column.field],
        change: function(args) {
          var totalCostValue = args.value * rowData['UnitPrice'];
          this.gridInstance.updateCell(rowIndex, 'TotalCost', totalCostValue);
        }.bind(this)
      });
      this.stockObj.appendTo(this.stockElem);
    }
  };

  public cellEdit (args) {
    if (args.columnName == 'TotalCost') {
      args.cancel = true;
    }
  }

  public priceElem: HTMLElement;
  public priceObj: NumericTextBox;

  public stockElem: HTMLElement;
  public stockObj: NumericTextBox;

  public render() {
    return <GridComponent dataSource={productData} ref={grid => this.gridInstance = grid} editSettings={this.editOptions} cellEdit={this.cellEdit} toolbar={this.toolbarOptions} height={273}>
        <ColumnsDirective>
          <ColumnDirective field="ProductID" headerText="Product ID" textAlign="Right" isPrimaryKey={true} width="100"/>
          <ColumnDirective field="ProductName" headerText="Product Name" width="120"/>
          <ColumnDirective field="UnitPrice" headerText="Unit Price" editType="numericedit"  edit={this.priceParams} width="150" format="C2" textAlign="Right"/>
          <ColumnDirective field="UnitsInStock" headerText="Units In Stock" editType="numericedit"  edit={this.stockParams} width="150" textAlign="Right"/>
          <ColumnDirective field="TotalCost" headerText="Total Cost" width="150" format="C2" textAlign="Right"/>
        </ColumnsDirective>
        <Inject services={[Edit, Toolbar]} />
    </GridComponent>
  }
};
```

{% endtab %}

## Dialog/Inline template

The Dialog/Inline template editing provides an option to customize the default behavior of dialog editing. Using the dialog template, you can render your own editors by defining the [`editSettings.mode`](../api/grid/editSettings/#mode) as **Dialog/Normal** and [`editSetting.template`](../api/grid/editSettings/#template) as a React component.

In some cases, you need to add the new field editors in the dialog which are not present in the column model. In that situation, the dialog template will help you to customize the default edit dialog.

In the following sample, grid enabled with dialog template editing.

{% tab template="grid/editing", sourceFiles="app/App.tsx,app/template.tsx,app/orderModel.tsx,app/datasource.tsx" %}

```typescript
import { setValue } from '@syncfusion/ej2-base';
import { ColumnDirective, ColumnsDirective, DialogEditEventArgs, Grid, GridComponent } from '@syncfusion/ej2-react-grids';
import { Edit, EditSettingsModel, Inject, Toolbar, ToolbarItems } from '@syncfusion/ej2-react-grids';
import * as React from 'react';
import { data } from './datasource';
import { IOrderModel } from './orderModel';
import { DialogFormTemplate } from './template';

export default class App extends React.Component<{}, {}> {
  public editOptions: EditSettingsModel = { allowAdding: true, allowDeleting: true, allowEditing: true, mode: 'Dialog',
  template: this.dialogTemplate };
  public toolbarOptions: ToolbarItems[] = ['Add', 'Edit', 'Delete'];
  public grid: Grid | null;

  public dialogTemplate(props: IOrderModel): any {
    return (<DialogFormTemplate {...props} />);
  }

  public actionComplete(args: DialogEditEventArgs): void {
    if (args.form) {
      if ((args.requestType === 'beginEdit' || args.requestType === 'add')) {
        /** Add Validation Rules */
          args.form.ej2_instances[0].addRules('Freight', {max: 500});
      }
      /** Set initial Focus */
      if (args.requestType === 'beginEdit') {
          (args.form.elements.namedItem('CustomerID') as HTMLInputElement).focus();
      } else if (args.requestType === 'add') {
          (args.form.elements.namedItem('OrderID')as HTMLInputElement).focus();
      }
    }
  }

  public actionBegin (args: DialogEditEventArgs) {
    if (args.requestType === 'save' && args.form) {
      /** cast string to integer value */
      setValue('data.Freight',
        parseFloat((args.form.querySelector("#Freight") as HTMLInputElement).value), args);
    }
  }

  public render() {
    this.actionComplete = this.actionComplete.bind(this);
    this.actionBegin = this.actionBegin.bind(this);
    return <GridComponent ref={g=> this.grid = g} dataSource={data} actionComplete={this.actionComplete}
      actionBegin={this.actionBegin} editSettings={this.editOptions} toolbar={this.toolbarOptions}
      height={265}>
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

> The Dialog/Inline template form editors should have **name** attribute.

### Template Context

The template should be a React Component class. You can access the row information inside the Component class using **props**, you can bind the attribute or value based on this row information.

The following properties will be available at the time of template execution.

| Property Name | Usage |
|---------------|-------|
| <kbd>isAdd</kbd> | A Boolean property; it defines whether the current row should be a new record or not. |

In the following code example, the **OrderID** textbox has been disabled by using the **isAdd** property.

```html
<!--The disabled attributes will be added based on the isAdd property.-->
<input id="OrderID" name="OrderID" type="text" disabled={!data.isAdd} value={data.OrderID} onChange={this.onChange} />

```

### Get value from editor

You can read, format, and update the current editor value in the [`actionBegin`](../api/grid/#actionbegin) event at the time of setting [`requestType`](../api/grid/saveEventArgs/#requesttype) to **save**.

In the following code example, the **Freight** value has been formatted and updated.

``` typescript
  public actionBegin (args: DialogEditEventArgs) {
    if (args.requestType === 'save' && args.form) {
      /** cast string to integer value */
      setValue('data.Freight',
        parseFloat((args.form.querySelector("#Freight") as HTMLInputElement).value), args);
    }
  }
```

### Set focus to editor

By default, the first input element in the dialog will be focused while opening the dialog.
If the first input element is in disabled or hidden state, focus the valid input element in the
[`actionComplete`](../api/grid/#actioncomplete)
event based on `requestType` as `beginEdit`.

```typescript

actionComplete(args: DialogEditEventArgs) {
        // Set initail Focus
        if (args.requestType === 'beginEdit') {
            (args.form.elements.namedItem('CustomerID')as HTMLInputElement).focus();
        }
    }

```

### Adding validation rules for custom editors

If you have used additional fields that are not present in the column model, then add the validation rules to the [`actionComplete`](../api/grid/#actioncomplete) event.

```typescript

  public actionComplete(args: DialogEditEventArgs) {
    if ((args.requestType === 'beginEdit' || args.requestType === 'add')) {
        /** Add Validation Rules */
        (args.form as HTMLFormElement).ej2_instances[0].addRules('Freight', {max: 500});
    }
  }

```

## Adding a new row at the Bottom of the Grid

By default, a new row will be added at the top of the grid. You can change it by setting [`editSettings.newRowPosition`](../api/grid/editSettings/#newrowposition) as **Bottom**.

{% tab template="grid/editing", sourceFiles="app/App.tsx,app/datasource.tsx" %}

```typescript
import { ColumnDirective, ColumnsDirective, GridComponent } from '@syncfusion/ej2-react-grids';
import { Edit, EditSettingsModel, Inject, Toolbar, ToolbarItems } from '@syncfusion/ej2-react-grids';
import * as React from 'react';
import { data } from './datasource';

export default class App extends React.Component<{}, {}> {
  public editOptions: EditSettingsModel = { allowEditing: true, allowAdding: true, allowDeleting: true, newRowPosition:'Bottom' };
  public toolbarOptions: ToolbarItems[] = ['Add', 'Edit', 'Delete', 'Update', 'Cancel'];

  public render() {
    return <GridComponent dataSource={data} editSettings={this.editOptions} toolbar={this.toolbarOptions} height={265}>
      <ColumnsDirective>
          <ColumnDirective field='OrderID' headerText='Order ID' width='100' textAlign="Right" isPrimaryKey={true}/>
          <ColumnDirective field='CustomerID' headerText='Customer ID' width='120'/>
          <ColumnDirective field='Freight' headerText='Freight' width='120' format="C2" editType= 'numericedit' textAlign="Right"/>
          <ColumnDirective field='ShipCountry' headerText='Ship Country' editType= 'dropdownedit' width='150'/>
      </ColumnsDirective>
      <Inject services={[Edit, Toolbar]} />
    </GridComponent>
  }
};
```

{% endtab %}

> Add [`editSettings.newRowPosition`](../api/grid/editSettings/#newrowposition) is supported for **Normal** and **Batch** editing modes.

## Command column

The command column provides an option to add CRUD action buttons in a column. This can be defined by the
 [`column.commands`](../api/grid/column/#commands) property.

The available built-in command buttons are:

| Command Button | Actions |
|----------------|---------|
| Edit | Edit the current row.|
| Delete | Delete the current row.|
| Save | Update the edited row.|
| Cancel | Cancel the edited state. |

{% tab template="grid/editing", sourceFiles="app/App.tsx,app/datasource.tsx" %}

```typescript
import { ColumnDirective, ColumnsDirective, CommandColumn, GridComponent } from '@syncfusion/ej2-react-grids';
import { CommandModel, Edit, EditSettingsModel, Inject } from '@syncfusion/ej2-react-grids';
import * as React from 'react';
import { data } from './datasource';

export default class App extends React.Component<{}, {}> {
  public editOptions: EditSettingsModel = { allowEditing: true, allowDeleting: true };
  public commands: CommandModel[] = [
    { type: 'Edit', buttonOption: { cssClass: 'e-flat', iconCss: 'e-edit e-icons' } },
    { type: 'Delete', buttonOption: { cssClass: 'e-flat', iconCss: 'e-delete e-icons' } },
    { type: 'Save', buttonOption: { cssClass: 'e-flat', iconCss: 'e-update e-icons' } },
    { type: 'Cancel', buttonOption: { cssClass: 'e-flat', iconCss: 'e-cancel-icon e-icons' } }
  ];

  public render() {
    return <GridComponent dataSource={data} editSettings={this.editOptions} height={265}>
      <ColumnsDirective>
          <ColumnDirective field='OrderID' headerText='Order ID' width='100' textAlign="Right" isPrimaryKey={true}/>
          <ColumnDirective field='CustomerID' headerText='Customer ID' width='120'/>
          <ColumnDirective field='Freight' headerText='Freight' width='120' format="C2" editType= 'numericedit' textAlign="Right"/>
          <ColumnDirective field='ShipCountry' headerText='Ship Country' editType= 'dropdownedit' width='150'/>
          <ColumnDirective headerText='Commands' width='120' commands= {this.commands}/>
      </ColumnsDirective>
      <Inject services={[Edit, CommandColumn]} />
    </GridComponent>
  }
};
```

{% endtab %}

### Custom command

 The custom command buttons can be added in a column by using the [`column.commands`](../api/grid/column/#commands) property and
the action for the custom buttons can be defined using [`commandClick`](../api/grid/#commandClick) event.

{% tab template="grid/editing", sourceFiles="app/App.tsx,app/datasource.tsx" %}

```typescript
import { closest } from '@syncfusion/ej2-base';
import { ColumnDirective, ColumnsDirective, CommandColumn, Grid, GridComponent } from '@syncfusion/ej2-react-grids';
import { Column, CommandModel, CommandClickEventArgs, Edit, EditSettingsModel, Inject, IRow } from '@syncfusion/ej2-react-grids';
import * as React from 'react';
import { data } from './datasource';

export default class App extends React.Component<{}, {}> {
  public editOptions: EditSettingsModel = { allowEditing: true, allowDeleting: true };
  public commands: CommandModel[] = [
    {
      buttonOption: {
        content: 'Details', cssClass: 'e-flat'
      }
    }
  ];
  public grid: Grid | null;

  public commandClick(args: CommandClickEventArgs): void  {
    if (this.grid) {
      alert(JSON.stringify(args.rowData));
    }
  }

  public render() {
  this.commandClick = this.commandClick.bind(this);
    return <GridComponent dataSource={data} editSettings={this.editOptions} commandClick={this.commandClick} height={265} ref={g => this.grid = g}>
      <ColumnsDirective>
          <ColumnDirective field='OrderID' headerText='Order ID' width='100' textAlign="Right" isPrimaryKey={true}/>
          <ColumnDirective field='CustomerID' headerText='Customer ID' width='120'/>
          <ColumnDirective field='Freight' headerText='Freight' width='120' format="C2" editType= 'numericedit' textAlign="Right"/>
          <ColumnDirective field='ShipCountry' headerText='Ship Country' editType= 'dropdownedit' width='150'/>
          <ColumnDirective headerText='Commands' width='120' commands= {this.commands}/>
      </ColumnsDirective>
      <Inject services={[Edit, CommandColumn]} />
    </GridComponent>
  }
};
```

{% endtab %}

## Confirmation messages

### Delete confirmation

The delete confirm dialog can be shown when deleting a record by defining the
[`showDeleteConfirmDialog`](../api/grid/editSettings/#showdeleteconfirmdialog) as **true**

{% tab template="grid/editing", sourceFiles="app/App.tsx,app/datasource.tsx" %}

```typescript
import { ColumnDirective, ColumnsDirective, GridComponent } from '@syncfusion/ej2-react-grids';
import { Edit, EditSettingsModel, Inject, Toolbar, ToolbarItems } from '@syncfusion/ej2-react-grids';
import * as React from 'react';
import { data } from './datasource';

export default class App extends React.Component<{}, {}> {
  public editOptions: EditSettingsModel = {
    allowAdding: true,
    allowDeleting: true,
    allowEditing: true,
    mode: 'Normal',
    showDeleteConfirmDialog: true
   };
  public toolbarOptions: ToolbarItems[] = ['Add', 'Edit', 'Delete', 'Update', 'Cancel'];

  public render() {
    return <GridComponent dataSource={data} editSettings={this.editOptions} toolbar={this.toolbarOptions} height={265} >
      <ColumnsDirective>
          <ColumnDirective field='OrderID' headerText='Order ID' width='100' textAlign="Right" isPrimaryKey={true}/>
          <ColumnDirective field='CustomerID' headerText='Customer ID' width='120'/>
          <ColumnDirective field='Freight' headerText='Freight' width='120' format="C2" editType= 'numericedit' textAlign="Right"/>
          <ColumnDirective field='ShipCountry' headerText='Ship Country' editType= 'dropdownedit' width='150'/>
      </ColumnsDirective>
      <Inject services={[Edit, Toolbar]} />
    </GridComponent>
  }
};
```

{% endtab %}

> The [`showDeleteConfirmDialog`](../api/grid/editSettings/#showdeleteconfirmdialog) supports all type of edit modes.

### Batch confirmation

By default, grid will show the confirm dialog when saving or cancelling or performing any actions like filtering, sorting, etc.

{% tab template="grid/editing", sourceFiles="app/App.tsx,app/datasource.tsx" %}

```typescript
import { ColumnDirective, ColumnsDirective, Filter, GridComponent, Sort } from '@syncfusion/ej2-react-grids';
import { Edit, EditSettingsModel, Inject, Toolbar, ToolbarItems } from '@syncfusion/ej2-react-grids';
import * as React from 'react';
import { data } from './datasource';

export default class App extends React.Component<{}, {}> {
  public editOptions: EditSettingsModel = {
    allowAdding: true,
    allowDeleting: true,
    allowEditing: true,
    mode: 'Batch',
    showConfirmDialog: true,
    showDeleteConfirmDialog: true
   };
  public toolbarOptions: ToolbarItems[] = ['Add', 'Edit', 'Delete', 'Update', 'Cancel'];

  public render() {
    return <GridComponent dataSource={data} allowFiltering={true} editSettings={this.editOptions}
      toolbar={this.toolbarOptions} allowSorting={true} height={265} >
      <ColumnsDirective>
          <ColumnDirective field='OrderID' headerText='Order ID' width='100' textAlign="Right" isPrimaryKey={true}/>
          <ColumnDirective field='CustomerID' headerText='Customer ID' width='120'/>
          <ColumnDirective field='Freight' headerText='Freight' width='120' format="C2" editType= 'numericedit' textAlign="Right"/>
          <ColumnDirective field='ShipCountry' headerText='Ship Country' editType= 'dropdownedit' width='150'/>
      </ColumnsDirective>
      <Inject services={[Edit, Toolbar, Sort, Filter]} />
    </GridComponent>
  }
};
```

{% endtab %}

> * [`editSettings.showConfirmDialog`](../api/grid/editSettings/#showconfirmdialog)
requires the [`editSettings.mode`](../api/grid/editSettings/#mode) to be **Batch**.
> * If [`editSettings.showConfirmDialog`](../api/grid/editSettings/#showconfirmdialog)
set to **false**, then confirmation dialog does not display in batch editing.

## Column validation

Column validation allows you to validate the edited or added row data and it display errors for invalid fields before saving data.
Grid uses **Form Validator** component for column validation.
You can set validation rules by defining the [`columns.validationRules`](../api/grid/column/#validationrules).

{% tab template="grid/editing", sourceFiles="app/App.tsx,app/datasource.tsx" %}

```typescript
import { ColumnDirective, ColumnsDirective, GridComponent } from '@syncfusion/ej2-react-grids';
import { Edit, EditSettingsModel, Inject, Toolbar, ToolbarItems } from '@syncfusion/ej2-react-grids';
import * as React from 'react';
import { data } from './datasource';

export default class App extends React.Component<{}, {}> {
  public editOptions: EditSettingsModel = { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Normal' };
  public toolbarOptions: ToolbarItems[] = ['Add', 'Edit', 'Delete', 'Update', 'Cancel'];
  public orderIDRules: object = { required: true, number: true };
  public customerIDRules: object = { required: true, minLength: 3 };

  public render() {
    return <GridComponent dataSource={data} editSettings={this.editOptions}
      toolbar={this.toolbarOptions} height={265} >
      <ColumnsDirective>
          <ColumnDirective field='OrderID' headerText='Order ID' validationRules={this.orderIDRules} width='100' textAlign="Right" isPrimaryKey={true}/>
          <ColumnDirective field='CustomerID' validationRules={this.customerIDRules} headerText='Customer ID' width='120'/>
          <ColumnDirective field='Freight' headerText='Freight' width='120' format="C2" editType= 'numericedit' textAlign="Right"/>
          <ColumnDirective field='ShipCountry' headerText='Ship Country' editType= 'dropdownedit' width='150'/>
      </ColumnsDirective>
      <Inject services={[Edit, Toolbar]} />
    </GridComponent>
  }
};
```

{% endtab %}

### Custom validation

You can define your own custom validation rules for the specific columns by using **Form Validator custom rules**.

In the below demo, custom validation applied for **CustomerID** column.

{% tab template="grid/editing", sourceFiles="app/App.tsx,app/datasource.tsx" %}

```typescript
import { getValue } from '@syncfusion/ej2-base';
import { ColumnDirective, ColumnsDirective, GridComponent } from '@syncfusion/ej2-react-grids';
import { Edit, EditSettingsModel, Inject, Toolbar, ToolbarItems } from '@syncfusion/ej2-react-grids';
import * as React from 'react';
import { data } from './datasource';

export default class App extends React.Component<{}, {}> {
  public editOptions: EditSettingsModel = { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Normal' };
  public toolbarOptions: ToolbarItems[] = ['Add', 'Edit', 'Delete', 'Update', 'Cancel'];

  public orderIDRules: object = { required: true };
  public customerIDRules: object = {
    minLength: [this.customFn, 'Need atleast 5 letters'],
    required: true
  };

  public customFn(args: { [key: string]: string }) : boolean {
      return getValue('value', args).length >= 5;
  };

  public render() {
    return <GridComponent dataSource={data} editSettings={this.editOptions}
      toolbar={this.toolbarOptions} height={265} >
      <ColumnsDirective>
          <ColumnDirective field='OrderID' headerText='Order ID' validationRules={this.orderIDRules} width='100' textAlign="Right" isPrimaryKey={true}/>
          <ColumnDirective field='CustomerID' defaultValue='HANAR' validationRules={this.customerIDRules} headerText='Customer ID' width='120'/>
          <ColumnDirective field='Freight' headerText='Freight' width='120' format="C2" editType= 'numericedit' textAlign="Right"/>
          <ColumnDirective field='ShipCountry' headerText='Ship Country' editType= 'dropdownedit' width='150'/>
      </ColumnsDirective>
      <Inject services={[Edit, Toolbar]} />
    </GridComponent>
  }
};
```

{% endtab %}

## Persisting data in server

Edited data can be persisted in the database using the RESTful web services.

All the CRUD operations in the grid are done through [`DataManager`](../data).
The **DataManager** has an option to bind all the CRUD related data in server-side.

> For your information, the ODataAdaptor persists data in the server as per OData protocol.

To learn about how to handle the CRUD actions in server side, you can check on this video for React Grid.

`youtube:TfqwtSjnQs8`

In the below section, we have explained how to get the edited data details on the server-side using the [`UrlAdaptor`](../../data/adaptors/#url-adaptor).

### URL adaptor

You can use the [`UrlAdaptor`](../../data/adaptors/#url-adaptor) of **DataManager** when binding data source from remote data.
In the initial load of grid, data are fetched from remote data and bound to the grid using **url** property of **DataManager**.
You can map The CRUD operation in grid can be mapped to server-side Controller actions using the properties **insertUrl**, **removeUrl**, **updateUrl**, **crudUrl** and **batchUrl**.

The following code example describes the above behavior.

```typescript
import { DataManager, UrlAdaptor } from '@syncfusion/ej2-data';
import { ColumnDirective, ColumnsDirective, GridComponent } from '@syncfusion/ej2-react-grids';
import { Edit, EditSettingsModel, Inject, Toolbar, ToolbarItems } from '@syncfusion/ej2-react-grids';
import * as React from 'react';

export default class App extends React.Component<{}, {}> {
  public editOptions: EditSettingsModel = { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Normal' };
  public toolbarOptions: ToolbarItems[] = ['Add', 'Edit', 'Delete', 'Update', 'Cancel'];
  public dataManager: DataManager = new DataManager({
    adaptor: new UrlAdaptor,
    insertUrl: "Home/Insert",
    removeUrl: "Home/Delete",
    updateUrl: "Home/Update",
    url: "Home/DataSource"
  });

  public render() {
    return <GridComponent dataSource={this.dataManager} editSettings={this.editOptions}
      toolbar={this.toolbarOptions} height={265} >
      <ColumnsDirective>
          <ColumnDirective field='OrderID' headerText='Order ID' width='100' textAlign="Right" isPrimaryKey={true}/>
          <ColumnDirective field='CustomerID' headerText='Customer ID' width='120'/>
          <ColumnDirective field='Freight' headerText='Freight' width='120' format="C2" editType= 'numericedit' textAlign="Right"/>
          <ColumnDirective field='ShipCountry' headerText='Ship Country' editType= 'dropdownedit' width='150'/>
      </ColumnsDirective>
      <Inject services={[Edit, Toolbar]} />
    </GridComponent>
  }
};
```

Also, when using the **UrlAdaptor**, you need to return the data as JSON from the controller action and the JSON object must contain a property as **result** with dataSource as its value and one more property **count** with the dataSource total records count as its value.

The following code example describes the above behavior.

```typescript
public ActionResult DataSource(DataManagerRequest dm)
{
    var DataSource = OrderRepository.GetAllRecords();
    DataResult result = new DataResult();
    result.result = DataSource.Skip(dm.Skip).Take(dm.Take).ToList();
    result.count = result.result.Count;
    return Json(result, JsonRequestBehavior.AllowGet);
}

public class DataResult
{
    public List<EditableOrder> result { get; set; }
    public int count { get; set; }
}

```

### Insert record

Using the **insertUrl** property, you can specify the controller action mapping URL to perform insert operation on the server-side.

The following code example describes the above behavior.

```typescript
public ActionResult Insert(EditableOrder value)
{
    //Insert record in database
}

```

The newly added record details are bound to the **value** parameter. Please refer to the following screenshot.

![Insert](images/insert.jpg)

### Update record

Using the **updateUrl** property, the controller action mapping URL can be specified to perform save/update operation on the server-side.

The following code example describes the previous behavior.

```typescript
public ActionResult Update(EditableOrder value)
{
    //Update record in database
}

```

The updated record details are bound to the **value** parameter. Please refer to the following screenshot.

![Update](images/update.jpg)

### Delete record

Using the **removeUrl** property, the controller action mapping URL can be specified to perform delete operation on the server-side.

The following code example describes the previous behavior.

```typescript
public ActionResult Delete(int key)
{
    //Delete record in database
}

```

The deleted record primary key value is bound to the **key** parameter. Please refer to the following screenshot.

![Delete](images/delete.jpg)

### CRUD URL

Using the **crudUrl** property, the controller action mapping URL can be specified to perform all the CRUD operation at server-side using a
single method instead of specifying separate controller action method for CRUD (insert, update and delete) operations.

The action parameter of **crudUrl** is used to get the corresponding CRUD action.

The following code example describes the above behavior.

```typescript
import { DataManager, UrlAdaptor } from '@syncfusion/ej2-data';
import { ColumnDirective, ColumnsDirective, GridComponent } from '@syncfusion/ej2-react-grids';
import { Edit, EditSettingsModel, Inject, Toolbar, ToolbarItems } from '@syncfusion/ej2-react-grids';
import * as React from 'react';

export default class App extends React.Component<{}, {}> {
  public editOptions: EditSettingsModel = { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Normal' };
  public toolbarOptions: ToolbarItems[] = ['Add', 'Edit', 'Delete', 'Update', 'Cancel'];
  public dataManager: DataManager = new DataManager({
    adaptor: new UrlAdaptor,
    crudUrl: "Home/CrudUpdate",
    url: "Home/DataSource"
  });


  public render() {
    return <GridComponent dataSource={this.dataManager} editSettings={this.editOptions}
      toolbar={this.toolbarOptions} height={265} >
      <ColumnsDirective>
          <ColumnDirective field='OrderID' headerText='Order ID' width='100' textAlign="Right" isPrimaryKey={true}/>
          <ColumnDirective field='CustomerID' headerText='Customer ID' width='120'/>
          <ColumnDirective field='Freight' headerText='Freight' width='120' format="C2" editType= 'numericedit' textAlign="Right"/>
          <ColumnDirective field='ShipCountry' headerText='Ship Country' editType= 'dropdownedit' width='150'/>
      </ColumnsDirective>
      <Inject services={[Edit, Toolbar]} />
    </GridComponent>
  }
};
```

```typescript
public ActionResult CrudUpdate(EditableOrder value, string action)
{
    if(action == "update"){
        //Update record in database
    }
    else if (action == "insert")
    {
        //Insert record in database
    }
    else
    {
        //Delete record in database
    }
}

```

Please refer to the following screenshot to know about the action parameter.

![CRUD update](images/crudupdate.jpg)

> If you specify `insertUrl` along with `crudUrl`, then while adding `insertUrl` only will be invoked.

### Batch URL

The **batchUrl** property supports only for batch editing mode.
You can specify the controller action mapping URL to perform batch operation on the server-side.

The following code example describes the above behavior.

```typescript
import { DataManager, UrlAdaptor } from '@syncfusion/ej2-data';
import { ColumnDirective, ColumnsDirective, GridComponent } from '@syncfusion/ej2-react-grids';
import { Edit, EditSettingsModel, Inject, Toolbar, ToolbarItems } from '@syncfusion/ej2-react-grids';
import * as React from 'react';
export default class App extends React.Component<{}, {}> {
  public editOptions: EditSettingsModel = { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Normal' };
  public toolbarOptions: ToolbarItems[] = ['Add', 'Edit', 'Delete', 'Update', 'Cancel'];
  public dataManager: DataManager = new DataManager({
    adaptor: new UrlAdaptor,
    batchUrl: "Home/BatchUpdate",
    url: "Home/DataSource"
  });

  public render() {
    return <GridComponent dataSource={this.dataManager} editSettings={this.editOptions}
      toolbar={this.toolbarOptions} height={265} >
      <ColumnsDirective>
          <ColumnDirective field='OrderID' headerText='Order ID' width='100' textAlign="Right" isPrimaryKey={true}/>
          <ColumnDirective field='CustomerID' headerText='Customer ID' width='120'/>
          <ColumnDirective field='Freight' headerText='Freight' width='120' format="C2" editType= 'numericedit' textAlign="Right"/>
          <ColumnDirective field='ShipCountry' headerText='Ship Country' editType= 'dropdownedit' width='150'/>
      </ColumnsDirective>
      <Inject services={[Edit, Toolbar]} />
    </GridComponent>
  }
};
```

```typescript
public ActionResult BatchUpdate(string action, List<EditableOrder> added, List<EditableOrder> changed, List<EditableOrder> deleted, int? key)
{
//Save the batch changes in database
}
```

![Batch](images/batch.jpg)

## Default column values on add new

The grid provides an option to set the default value for the columns when adding a new record in it.
To set a default value for the particular column by defining the [`columns.defaultValue`](../api/grid/column/#defaultvalue).

{% tab template="grid/editing", sourceFiles="app/App.tsx,app/datasource.tsx" %}

```typescript
import { ColumnDirective, ColumnsDirective, GridComponent } from '@syncfusion/ej2-react-grids';
import { Edit, EditSettingsModel, Inject, Toolbar, ToolbarItems } from '@syncfusion/ej2-react-grids';
import * as React from 'react';
import { data } from './datasource';

export default class App extends React.Component<{}, {}> {
  public editOptions: EditSettingsModel = { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Normal' };
  public toolbarOptions: ToolbarItems[] = ['Add', 'Edit', 'Delete', 'Update', 'Cancel'];
  public orderIDRules: object = { required: true };
  public customerIDRules: object = { required: true, minLength: 3 };

  public render() {
    return <GridComponent dataSource={data} editSettings={this.editOptions}
      toolbar={this.toolbarOptions} height={265} >
      <ColumnsDirective>
          <ColumnDirective field='OrderID' headerText='Order ID' validationRules={this.orderIDRules} width='100' textAlign="Right" isPrimaryKey={true}/>
          <ColumnDirective field='CustomerID' defaultValue='HANAR' validationRules={this.customerIDRules} headerText='Customer ID' width='120'/>
          <ColumnDirective field='Freight' headerText='Freight' width='120' format="C2" editType= 'numericedit' textAlign="Right"/>
          <ColumnDirective field='ShipCountry' headerText='Ship Country' editType= 'dropdownedit' width='150'/>
      </ColumnsDirective>
      <Inject services={[Edit, Toolbar]} />
    </GridComponent>
  }
};
```

{% endtab %}

## Disable editing for particular column

You can disable editing for particular columns by using the [`columns.allowEditing`](../api/grid/column/#allowediting).

In the following demo, editing is disabled for the **CustomerID** column.

{% tab template="grid/editing", sourceFiles="app/App.tsx,app/datasource.tsx" %}

```typescript
import { ColumnDirective, ColumnsDirective, GridComponent } from '@syncfusion/ej2-react-grids';
import { Edit, EditSettingsModel, Inject, Toolbar, ToolbarItems } from '@syncfusion/ej2-react-grids';
import * as React from 'react';
import { data } from './datasource';

export default class App extends React.Component<{}, {}> {
  public editOptions: EditSettingsModel = { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Normal' };
  public toolbarOptions: ToolbarItems[] = ['Add', 'Edit', 'Delete', 'Update', 'Cancel'];
  public orderIDRules: object = { required: true };
  public customerIDRules: object = { required: true, minLength: 3 };

  public render() {
    return <GridComponent dataSource={data} editSettings={this.editOptions}
      toolbar={this.toolbarOptions} height={265} >
      <ColumnsDirective>
          <ColumnDirective field='OrderID' headerText='Order ID' validationRules={this.orderIDRules} width='100' textAlign="Right" isPrimaryKey={true}/>
          <ColumnDirective field='CustomerID' allowEditing={false} validationRules={this.customerIDRules} headerText='Customer ID' width='120'/>
          <ColumnDirective field='Freight' headerText='Freight' width='120' format="C2" editType= 'numericedit' textAlign="Right"/>
          <ColumnDirective field='ShipCountry' headerText='Ship Country' editType= 'dropdownedit' width='150'/>
      </ColumnsDirective>
      <Inject services={[Edit, Toolbar]} />
    </GridComponent>
  }
};
```

{% endtab %}

## Troubleshoot: Editing works only for first row

The Editing functionalities can be performed based upon the primary key value of the selected row.
If `primaryKey` is not defined in the grid, then edit or delete action take places the first row.

## See also

* [Customize dialog when editing](./how-to/customize-the-edit-dialog)
* [Cascading DropDownList with Grid Editing](./how-to/cascading-drop-down-list-with-grid-editing)
* [Customize the Edit Dialog](./how-to/customize-the-edit-dialog)
* [Wizard Like Editing](./how-to/use-wizard-like-dialog-editing)
* [Tab Inside the Dialog Template](./how-to/using-tab-inside-the-dialog-editing)
* [Restrict to type decimal points in a NumericTextBox while editing the numeric column](./how-to/restrict-decimal-points-while-grid-editing)