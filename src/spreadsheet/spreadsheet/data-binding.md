---
title: "Data Binding"
component: "Spreadsheet"
description: "Learn how to bind local and remote data in the Essential JS 2 Spreadsheet control."
---

# Data Binding

The Spreadsheet uses [`DataManager`](../data), which supports both RESTful JSON data services and local JavaScript object array binding to a range. The `dataSource` property can be assigned either with the instance of [`DataManager`](../data) or JavaScript object array collection.

> To bind data to a cell, use `cell data binding` support.

## Local data

To bind local data to the Spreadsheet, you can assign a JavaScript object array to the `dataSource` property.

Refer to the following code example for local data binding.

{% tab template="spreadsheet/local-data-binding", sourceFiles="app/**/*.tsx,index.html", iframeHeight="450px", isDefaultActive=true, compileJsx=true %}

```tsx
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { SpreadsheetComponent, SheetsDirective, SheetDirective, RangesDirective } from '@syncfusion/ej2-react-spreadsheet';
import { data } from './datasource';
import { RangeDirective, ColumnsDirective, ColumnDirective } from '@syncfusion/ej2-react-spreadsheet';
export default class App extends React.Component<{}, {}> {
    spreadsheet: SpreadsheetComponent;
     render() {
        return  (<SpreadsheetComponent ref={(ssObj) => { this.spreadsheet = ssObj }}>
                        <SheetsDirective>
                            <SheetDirective>
                                <RangesDirective>
                                    <RangeDirective dataSource={data}></RangeDirective>
                                </RangesDirective>
                                <ColumnsDirective>
                                    <ColumnDirective width={100}></ColumnDirective>
                                    <ColumnDirective width={110}></ColumnDirective>
                                    <ColumnDirective width={100}></ColumnDirective>
                                    <ColumnDirective width={180}></ColumnDirective>
                                    <ColumnDirective width={130}></ColumnDirective>
                                    <ColumnDirective width={130}></ColumnDirective>
                                </ColumnsDirective>
                            </SheetDirective>
                        </SheetsDirective>
                    </SpreadsheetComponent>);
    }
}
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

> The local data source can also be provided as an instance of the [`DataManager`](../data). By default, [`DataManager`](../data) uses **JsonAdaptor** for local data-binding.

## Remote data

To bind remote data to the Spreadsheet control, assign service data as an instance of [`DataManager`](../data) to the `dataSource` property. To interact with remote data source, provide the service endpoint `url`.

Refer to the following code example for remote data binding.

{% tab template="spreadsheet/remote-data-binding", sourceFiles="app/**/*.tsx,index.html", iframeHeight="450px", isDefaultActive=true, compileJsx=true %}

```tsx
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { DataManager, Query } from '@syncfusion/ej2-data';
import { SpreadsheetComponent, SheetsDirective, SheetDirective, RangesDirective } from '@syncfusion/ej2-react-spreadsheet';
import { RangeDirective, ColumnsDirective, ColumnDirective } from '@syncfusion/ej2-react-spreadsheet';

export default class App extends React.Component<{}, {}> {
    public query: Query = new Query().select(['OrderID', 'CustomerID', 'ShipName', 'ShipCity', 'ShipCountry', 'Freight']).take(200);
    public data: DataManager = new DataManager({
        url: 'https://js.syncfusion.com/demos/ejServices//wcf/Northwind.svc/Orders',
        crossDomain: true
    });
    spreadsheet: SpreadsheetComponent;
     render() {
        return  (<SpreadsheetComponent ref={(ssObj) => { this.spreadsheet = ssObj }}>
                        <SheetsDirective>
                            <SheetDirective name= 'Shipment Details'>
                                <RangesDirective>
                                    <RangeDirective dataSource={this.data} query={this.query}></RangeDirective>
                                </RangesDirective>
                                <ColumnsDirective>
                                    <ColumnDirective width={100}></ColumnDirective>
                                    <ColumnDirective width={110}></ColumnDirective>
                                    <ColumnDirective width={100}></ColumnDirective>
                                    <ColumnDirective width={180}></ColumnDirective>
                                    <ColumnDirective width={130}></ColumnDirective>
                                    <ColumnDirective width={130}></ColumnDirective>
                                </ColumnsDirective>
                            </SheetDirective>
                        </SheetsDirective>
                    </SpreadsheetComponent>);
    }
}
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

> By default, `DataManager` uses **ODataAdaptor** for remote data-binding.

## Cell data binding

The Spreadsheet control can bind the data to individual cell in a sheet . To achive this you can use the
`value` property.

Refer to the following code example for cell data binding.

{% tab template="spreadsheet/cell-data-binding", sourceFiles="app/**/*.tsx,index.html", iframeHeight="450px", isDefaultActive=true, compileJsx=true %}

```tsx
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { SpreadsheetComponent, SheetsDirective, SheetDirective, RowsDirective, CellsDirective, RowDirective, CellDirective } from '@syncfusion/ej2-react-spreadsheet';
import { ColumnsDirective, ColumnDirective } from '@syncfusion/ej2-react-spreadsheet';

export default class App extends React.Component<{}, {}> {
    spreadsheet: SpreadsheetComponent;
     render() {
        return  (<SpreadsheetComponent ref={(ssObj) => { this.spreadsheet = ssObj }}>
        <SheetsDirective>
            <SheetDirective selectedRange='D13' name='PriceDetails'>
                <RowsDirective>
                    <RowDirective>
                        <CellsDirective>
                            <CellDirective value='Item Name' ></CellDirective>
                            <CellDirective value='Quantity' ></CellDirective>
                            <CellDirective value='Price' ></CellDirective>
                            <CellDirective value='Amount' ></CellDirective>
                            <CellDirective value='Stock Detail' ></CellDirective>
                            <CellDirective value='Website' ></CellDirective>
                        </CellsDirective>
                    </RowDirective>
                    <RowDirective>
                        <CellsDirective>
                            <CellDirective value='Casual Shoes' ></CellDirective>
                            <CellDirective value='10' ></CellDirective>
                            <CellDirective value='$20' ></CellDirective>
                            <CellDirective value='$200' ></CellDirective>
                            <CellDirective value='OUT OF STOCK' ></CellDirective>
                            <CellDirective value='Amazon'></CellDirective>
                        </CellsDirective>
                    </RowDirective>
                    <RowDirective>
                        <CellsDirective>
                            <CellDirective value='Sports Shoes' ></CellDirective>
                            <CellDirective value='20' ></CellDirective>
                            <CellDirective value='$30' ></CellDirective>
                            <CellDirective value='$600'></CellDirective>
                            <CellDirective value='IN STOCK'></CellDirective>
                            <CellDirective value='Overstack'></CellDirective>
                        </CellsDirective>
                    </RowDirective>
                    <RowDirective>
                        <CellsDirective>
                            <CellDirective value='Formal Shoes' ></CellDirective>
                            <CellDirective value='20' ></CellDirective>
                            <CellDirective value='$15' ></CellDirective>
                            <CellDirective value='$300'></CellDirective>
                            <CellDirective value='IN STOCK'></CellDirective>
                            <CellDirective value='AliExpress'></CellDirective>
                        </CellsDirective>
                    </RowDirective>
                    <RowDirective>
                        <CellsDirective>
                            <CellDirective value='Sandals & Floaters' ></CellDirective>
                            <CellDirective value='15' ></CellDirective>
                            <CellDirective value='$20' ></CellDirective>
                            <CellDirective value='$300' ></CellDirective>
                            <CellDirective value='OUT OF STOCK' ></CellDirective>
                            <CellDirective value='AliBaba'></CellDirective>
                        </CellsDirective>
                    </RowDirective>
                    <RowDirective>
                        <CellsDirective>
                            <CellDirective value='Flip-Flops & Slippers' ></CellDirective>
                            <CellDirective value='30' ></CellDirective>
                            <CellDirective value='$10' ></CellDirective>
                            <CellDirective value='$300'></CellDirective>
                            <CellDirective value='IN STOCK' ></CellDirective>
                            <CellDirective value='Taobao'></CellDirective>
                        </CellsDirective>
                    </RowDirective>
                </RowsDirective>
                <ColumnsDirective>
                    <ColumnDirective width={110}></ColumnDirective>
                    <ColumnDirective width={115}></ColumnDirective>
                    <ColumnDirective width={110}></ColumnDirective>
                    <ColumnDirective width={100}></ColumnDirective>
                    <ColumnDirective width={110}></ColumnDirective>
                    <ColumnDirective width={100}></ColumnDirective>
                </ColumnsDirective>
            </SheetDirective>
        </SheetsDirective>
    </SpreadsheetComponent>);
    }
}
ReactDOM.render(<App />, document.getElementById('root'));
```

{% endtab %}

> The cell data binding also supports formula, style, number format, and more.

## See Also

* [Filtering](./filter)
* [Sorting](./sort)
* [Hyperlink](./link)
* [`Collaborative Editing`](use-cases/collaborative-editing)