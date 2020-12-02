---
title: "Data Binding"
component: "QueryBuilder"
description: "Learn how to bind local data in the Essential JS 2 QueryBuilder control."
---

# Data Binding

The Query Builder uses `DataManager`, which supports both RESTful JSON data services binding and local JavaScript object array binding. The `dataSource` property can be assigned either with the instance of `DataManager` or JavaScript object array collection. It supports two kind of databinding method:

* Local data
* Remote data

## Local data

To bind local data to the query builder, you can assign the [`dataSource`](https://ej2.syncfusion.com/react/documentation/api/query-builder/#datasource) property  with a JavaScript object array. The local data source can also be provided as an instance of the `DataManager`.

{% tab template="query-builder/default", sourceFiles="app/**/*.tsx,index.html,datasource.ts", isDefaultActive=true, compileJsx=true %}

```tsx
import { ColumnsModel, QueryBuilderComponent, RuleModel } from '@syncfusion/ej2-react-querybuilder';
import * as React from 'react';
import * as ReactDom from 'react-dom';
// @ts-ignore
import { employeeData } from '../datasource.ts';

class App extends React.Component<{}, {}> {

    public columnData: ColumnsModel[] = [
        { field: 'EmployeeID', label: 'EmployeeID', type: 'number'},
        { field: 'FirstName', label: 'FirstName', type: 'string' },
        { field: 'TitleOfCourtesy', label: 'Title Of Courtesy', type: 'boolean', values: ['Mr.', 'Mrs.'] },
        { field: 'Title', label: 'Title', type: 'string' },
        { field: 'HireDate', label: 'HireDate', type: 'date', format: 'dd/MM/yyyy' },
        { field: 'Country', label: 'Country', type: 'string' },
        { field: 'City', label: 'City', type: 'string' }
    ];
    public importRules: RuleModel = {
        'condition': 'and',
        'rules': [{
            'field': 'EmployeeID',
            'label': 'EmployeeID',
            'operator': 'equal',
            'type': 'number',
            'value': 1
        },
        {
            'field': 'Title',
            'label': 'Title',
            'operator': 'equal',
            'type': 'string',
            'value': 'Sales Manager'
        }]
    };

    public render() {
        return (
                <QueryBuilderComponent width='100%' dataSource={employeeData} columns={this.columnData} rule={this.importRules} />
        );
    }
}
ReactDom.render(<App />,document.getElementById('querybuilder'));
```

{% endtab %}

> By default, `DataManager` uses `JsonAdaptor` for local data-binding.

## Remote data

To bind remote  data to the query builder, assign service data as an instance of  `DataManager` to the [`dataSource`](https://ej2.syncfusion.com/documentation/api/query-builder/#datasource) property. To interact with remote data source, provide the endpoint `url`.

{% tab template="query-builder/default", sourceFiles="app/**/*.tsx,index.html,datasource.ts", isDefaultActive=true, compileJsx=true %}

```tsx
import * as React from 'react';
import * as ReactDom from 'react-dom';
import { QueryBuilderComponent, ColumnsModel, RuleModel } from '@syncfusion/ej2-react-querybuilder';
import { DataManager, ODataAdaptor } from '@syncfusion/ej2-data';

export default class App extends React.Component<{}, {}> {
          public data = new DataManager({
          url: 'https://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Orders/',
      });

    columnData: ColumnsModel[] = [
        { field: 'EmployeeID', label: 'EmployeeID', type: 'number'},
        { field: 'FirstName', label: 'FirstName', type: 'string' },
        { field: 'TitleOfCourtesy', label: 'Title Of Courtesy', type: 'boolean', values: ['Mr.', 'Mrs.'] },
        { field: 'Title', label: 'Title', type: 'string' },
        { field: 'HireDate', label: 'HireDate', type: 'date', format: 'dd/MM/yyyy' },
        { field: 'Country', label: 'Country', type: 'string' },
        { field: 'City', label: 'City', type: 'string' }
    ];
    importRules: RuleModel = {
        'condition': 'and',
        'rules': [{
            'label': 'EmployeeID',
            'field': 'EmployeeID',
            'type': 'number',
            'operator': 'equal',
            'value': 1
        },
        {
            'label': 'Title',
            'field': 'Title',
            'type': 'string',
            'operator': 'equal',
            'value': 'Sales Manager'
        }]
    };

    render() {
        return (
                <QueryBuilderComponent width='100%' dataSource={this.data} columns={this.columnData} rule={this.importRules} ></QueryBuilderComponent>
        );
    }
}
ReactDom.render(<App />,document.getElementById('querybuilder'));
```

{% endtab %}

> By default, `DataManager` uses `ODataAdaptor` for remote data-binding.

### Binding with OData services

[`OData`](https://www.odata.org/documentation/odata-version-3-0/) is a standardized protocol for creating and consuming data. You can retrieve data from OData service using the DataManager. Refer to the following code example for remote Data binding using OData service.

{% tab template="query-builder/default", sourceFiles="app/**/*.tsx,index.html,datasource.ts", isDefaultActive=true, compileJsx=true %}

```tsx
import * as React from 'react';
import * as ReactDom from 'react-dom';
import { QueryBuilderComponent, ColumnsModel, RuleModel } from '@syncfusion/ej2-react-querybuilder';
import { DataManager, ODataAdaptor } from '@syncfusion/ej2-data';

export default class App extends React.Component<{}, {}> {
             public data = new DataManager({
             url: 'https://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Orders/',
             adaptor: new ODataAdaptor,
             crossDomain: true
          });

    columnData: ColumnsModel[] = [
        { field: 'EmployeeID', label: 'EmployeeID', type: 'number'},
        { field: 'FirstName', label: 'FirstName', type: 'string' },
        { field: 'TitleOfCourtesy', label: 'Title Of Courtesy', type: 'boolean', values: ['Mr.', 'Mrs.'] },
        { field: 'Title', label: 'Title', type: 'string' },
        { field: 'HireDate', label: 'HireDate', type: 'date', format: 'dd/MM/yyyy' },
        { field: 'Country', label: 'Country', type: 'string' },
        { field: 'City', label: 'City', type: 'string' }
    ];
    public importRules: RuleModel = {
        'condition': 'and',
        'rules': [{
            'field': 'EmployeeID',
            'label': 'EmployeeID',
            'operator': 'equal',
            'type': 'number',
            'value': 1
        },
        {
            'field': 'Title',
            'label': 'Title',
            'operator': 'equal',
            'type': 'string',
            'value': 'Sales Manager'
        }]
    };

    public render() {
        return (
                <QueryBuilderComponent width='100%' dataSource={this.data} columns={this.columnData} rule={this.importRules} ></QueryBuilderComponent>
        );
    }
}
ReactDom.render(<App />,document.getElementById('querybuilder'));
```

{% endtab %}

### Binding with OData v4 services

The ODataV4 is an improved version of OData protocols, and the `DataManager` can also retrieve and consume OData v4 services. For more details on OData v4 services, refer to the [`odata documentation`](http://docs.oasis-open.org/odata/odata/v4.0/errata03/os/complete/part1-protocol/odata-v4.0-errata03-os-part1-protocol-complete.html#_Toc453752197). To bind OData v4 service, use the `ODataV4Adaptor`.

{% tab template="query-builder/default", sourceFiles="app/**/*.tsx,index.html,datasource.ts", isDefaultActive=true, compileJsx=true %}

```tsx
import * as React from 'react';
import * as ReactDom from 'react-dom';
import { QueryBuilderComponent, ColumnsModel, RuleModel } from '@syncfusion/ej2-react-querybuilder';
import { DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

export default class App extends React.Component<{}, {}> {
                 public data = new DataManager({
                 url: 'https://services.odata.org/V4/Northwind/Northwind.svc/Orders/',
                 adaptor: new ODataV4Adaptor
           });

    columnData: ColumnsModel[] = [
        { field: 'EmployeeID', label: 'EmployeeID', type: 'number'},
        { field: 'FirstName', label: 'FirstName', type: 'string' },
        { field: 'TitleOfCourtesy', label: 'Title Of Courtesy', type: 'boolean', values: ['Mr.', 'Mrs.'] },
        { field: 'Title', label: 'Title', type: 'string' },
        { field: 'HireDate', label: 'HireDate', type: 'date', format: 'dd/MM/yyyy' },
        { field: 'Country', label: 'Country', type: 'string' },
        { field: 'City', label: 'City', type: 'string' }
    ];
    importRules: RuleModel = {
        'condition': 'and',
        'rules': [{
            'label': 'EmployeeID',
            'field': 'EmployeeID',
            'type': 'number',
            'operator': 'equal',
            'value': 1
        },
        {
            'label': 'Title',
            'field': 'Title',
            'type': 'string',
            'operator': 'equal',
            'value': 'Sales Manager'
        }]
    };

    render() {
        return (
                <QueryBuilderComponent width='100%' dataSource={this.data} columns={this.columnData} rule={this.importRules} ></QueryBuilderComponent>
        );
    }
}
ReactDom.render(<App />,document.getElementById('querybuilder'));
```

{% endtab %}

### Web API

You can use `WebApiAdaptor` to bind query builder with Web API created using OData endpoint.

{% tab compileJsx=true%}

```tsx
import * as React from 'react';
import * as ReactDom from 'react-dom';
import { QueryBuilderComponent, ColumnsModel, RuleModel } from '@syncfusion/ej2-react-querybuilder';

export default class App extends React.Component<{}, {}> {
                 public data = new DataManager({
                 url: '/api/OrderAPI',
                 adaptor: new WebApiAdaptor
          });

    columnData: ColumnsModel[] = [
        { field: 'EmployeeID', label: 'EmployeeID', type: 'number'},
        { field: 'FirstName', label: 'FirstName', type: 'string' },
        { field: 'TitleOfCourtesy', label: 'Title Of Courtesy', type: 'boolean', values: ['Mr.', 'Mrs.'] },
        { field: 'Title', label: 'Title', type: 'string' },
        { field: 'HireDate', label: 'HireDate', type: 'date', format: 'dd/MM/yyyy' },
        { field: 'Country', label: 'Country', type: 'string' },
        { field: 'City', label: 'City', type: 'string' }
    ];
    importRules: RuleModel = {
        'condition': 'and',
        'rules': [{
            'label': 'EmployeeID',
            'field': 'EmployeeID',
            'type': 'number',
            'operator': 'equal',
            'value': 1
        },
        {
            'label': 'Title',
            'field': 'Title',
            'type': 'string',
            'operator': 'equal',
            'value': 'Sales Manager'
        }]
    };

    render() {
        return (
                <QueryBuilderComponent width='100%' dataSource={this.data} columns={this.columnData} rule={this.importRules} ></QueryBuilderComponent>
        );
    }
}
ReactDom.render(<App />,document.getElementById('querybuilder'));
```

{% endtab %}

## Data Manager

You can use the created conditions in DataManager through the getPredicate method. This method creates predicates which is used as conditions in DataManager. In this example given below, `getValidRules` method is used to get the valid queried data.

{% tab template="query-builder/datamanager", sourceFiles="app/**/*.tsx,index.html,datasource.ts", isDefaultActive=true, compileJsx=true %}

```tsx
import { DataManager, Query } from '@syncfusion/ej2-data';
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { ColumnsModel, QueryBuilderComponent, RuleModel } from '@syncfusion/ej2-react-querybuilder';
import * as React from 'react';
import * as ReactDom from 'react-dom';
// @ts-ignore
import { hardwareData } from '../datasource.ts';

class App extends React.Component<{}, {result: any [], style: any}> {
    public qryBldrObj: QueryBuilderComponent;
    public columnData: ColumnsModel[] = [
        { field: 'TaskID', label: 'Task ID', type: 'number' },
        { field: 'Name', label: 'Name', type: 'string' },
        { field: 'Category', label: 'Category', type: 'string' },
        { field: 'SerialNo', label: 'Serial No', type: 'string' },
        { field: 'InvoiceNo', label: 'Invoice No', type: 'string' },
        { field: 'Status', label: 'Status', type: 'string' }
    ];
    public importRules: RuleModel = {
        'condition': 'or',
        'rules': [{
            'field': 'TaskID',
            'label': 'Task ID',
            'operator': 'equal',
            'type': 'number',
            'value': 1
        }]
    };
    constructor(props: any) {
        super(props);
        this.onClick = this.onClick.bind(this);
        this.state = {result: [], style: {display: 'none'} };
    }
    public onClick(): void {
        const validRule = this.qryBldrObj.getValidRules(this.qryBldrObj.rule);
        const dataManagerQuery = new Query().select(['TaskID', 'Category', 'Status']).where(this.qryBldrObj.getPredicate(validRule)).take(8);
        this.setState({result: new DataManager(hardwareData).executeLocal(dataManagerQuery), style: {display: 'block'}});
    }

    public render() {
        return (
            <div>
                <QueryBuilderComponent width='100%' dataSource={hardwareData} columns={this.columnData}  rule={this.importRules}
                    ref={(scope) => { this.qryBldrObj = scope as QueryBuilderComponent; }}/>
                <div className="e-qb-button">
                    <ButtonComponent id="getdata" cssClass='e-primary' content='get data' onClick = {this.onClick} />
                </div>
                <table id="datatable" className="e-table" style={this.state.style}>
                    <thead>
                        <tr><th>TaskID</th><th>Category</th><th>Status</th></tr>
                    </thead>
                    <tbody>{this.state.result.map(function func(item, key) {
                        return (
                            <tr key = {key}>
                                <td>{item.TaskID}</td>
                                <td>{item.Category}</td>
                                <td>{item.Status}</td>
                            </tr>
                        )
                    })}</tbody>
                </table>
            </div>
        );
    }
}

ReactDom.render(<App />,document.getElementById('querybuilder'));
```

{% endtab %}