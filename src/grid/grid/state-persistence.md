---
title: "State Persistence"
component: "Grid"
description: "Learn how to persist the DataGrid state and model in the browser’s local storage."
---

# State Persistence

State persistence refers to the Grid's state maintained in the browser's [`localStorage`](https://www.w3schools.com/html/html5_webstorage.asp#) even if the browser is refreshed or if you move to the next page within the browser.
State persistence stores grid’s model object in the local storage when the [`enablePersistence`](../api/grid/#enablepersistence) is defined as true.

## Maintaining Custom Query in State Persistence

The grid does not maintain the query params after page load event when the [`enablePersistence`](../api/grid/#enablepersistence) is set to true.
This is because the grid refreshes its query params for every page load. You can maintain the custom query params by resetting the [`addParams`](https://ej2.syncfusion.com/documentation/api/data/query/#addparams) method of Grid [`query`](../api/grid/#query) in the [`actionBegin`](../api/grid/#actionbegin) event.

{% tab template="grid/column", sourceFiles="app/App.tsx,app/datasource.tsx" %}

```typescript
import { ColumnDirective, ColumnsDirective, GridComponent } from '@syncfusion/ej2-react-grids';
import { ActionEventArgs, Filter, Grid, Inject, Page  } from '@syncfusion/ej2-react-grids';
import * as React from 'react';
import { data } from './datasource';

export default class App extends React.Component<{}, {}>{
  private grid: Grid | null;
  public actionHandler(args: ActionEventArgs){
    if (this.grid) {
      this.grid.query.addParams('$filter', 'EmployeeID eq 1');
    }
  }

  public render() {
      this.actionHandler = this.actionHandler.bind(this);
      return <GridComponent dataSource={data} allowFiltering={true} allowPaging={true} enablePersistence={true} height={230}
      actionBegin={this.actionHandler} ref={g => this.grid = g}>
          <ColumnsDirective>
              <ColumnDirective field='OrderID' width='100' textAlign="Right"/>
              <ColumnDirective field='CustomerID' width='100'/>
              <ColumnDirective field='EmployeeID' width='100' textAlign="Right"/>
              <ColumnDirective field='Freight' width='100' format="C2" textAlign="Right"/>
              <ColumnDirective field='ShipCountry' width='100'/>
          </ColumnsDirective>
          <Inject services={[Filter, Page]} />
      </GridComponent>
  }
};
```

{% endtab %}

## How to get or set localStorage value

If the [`enablePersistence`](../api/grid/#enablepersistence) property is set to **true**, the grid property value is saved in the **window.localStorage** for reference.
You can get/set the localStorage value by using the **getItem/setItem** method in the **window.localStorage**.

```typescript
    /** get the Grid model
     * "gridGrid" is component name + component id
     */
    const value: string = window.localStorage.getItem('gridGrid');
    const model: object = JSON.parse(value);
```

```typescript
  /** set the Grid model
   * "gridGrid" is component name + component id
   */
  window.localStorage.setItem('gridGrid', JSON.stringify(model));
```

## Restore initial Grid state

When the [`enablePersistence`](../api/grid/#enablepersistence) property is set to **true**, the Grid will keep its state even if the page is reloaded. In some cases, you may be required to retain the Grid in its initial state. The Grid will not retain its initial state now since the [`enablePersistence`](../api/grid/#enablepersistence) property has been enabled.

You can achieve this by destroying the grid after disabling the [`enablePersistence`](../api/grid/#enablepersistence) property and clearing the local storage data, as shown in the sample below.

{% tab template="grid/column", sourceFiles="app/App.tsx,app/datasource.tsx" %}

```typescript
import { ColumnDirective, ColumnsDirective, GridComponent } from '@syncfusion/ej2-react-grids';
import { ActionEventArgs, Filter, Grid, Inject, Page  } from '@syncfusion/ej2-react-grids';
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import * as React from 'react';
import { data } from './datasource';

export default class App extends React.Component<{}, {}>{
  private grid: Grid | null;
  public clickHandler(){
      this.grid.enablePersistence = false;
      window.localStorage.setItem("gridGrid", "");
      this.grid.destroy();
      //reloads the page
      location.reload();
  }
  public render() {
      this.clickHandler = this.clickHandler.bind(this);
      return( <div> <ButtonComponent onClick= { this.clickHandler }>Restore to initial state</ButtonComponent> <GridComponent id="Grid" dataSource={data} allowFiltering={true} allowPaging={true} enablePersistence={true} height={230}
      ref={g => this.grid = g}>
          <ColumnsDirective>
              <ColumnDirective field='OrderID' width='100' textAlign="Right"/>
              <ColumnDirective field='CustomerID' width='100'/>
              <ColumnDirective field='EmployeeID' width='100' textAlign="Right"/>
              <ColumnDirective field='Freight' width='100' format="C2" textAlign="Right"/>
              <ColumnDirective field='ShipCountry' width='100'/>
          </ColumnsDirective>
          <Inject services={[Filter, Page]} />
      </GridComponent></div>)
  }
};
```

{% endtab %}