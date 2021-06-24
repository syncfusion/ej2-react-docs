---
title: " Chart How To | TypeScript "

component: "Chart"

description: "How to section explains knowledge base samples and howto access different types properties and events of the chart."
---

# Visualize the data that returned by grid in chart

You can visualize the data that returned by grid in chart.

To visualize the data in chart, follow the given steps:

**Step 1**:

Initialize the grid with datasource.

**Step 2**:

By using the grid’s `actionComplete` event and `getCurrentViewRecords` method, you can get the current page records.
By using the grid’s `databound` event, you can update the current page records into the chart’s datasource and visualize the grid data in chart.

{% tab template="chart/grid-visual", sourceFiles="app/**/*.tsx,app/datasource.ts" %}

```typescript
import React from 'react';
import * as ReactDOM from "react-dom";
import {
  ChartComponent, SeriesCollectionDirective, SeriesDirective, Inject, AxisModel, Chart, ColumnSeries, DateTime
} from '@syncfusion/ej2-react-charts';
import { ColumnDirective, ColumnsDirective, GridComponent, Page, PageSettingsModel, Selection, Grid } from '@syncfusion/ej2-react-grids';
import { DataManager, Query } from '@syncfusion/ej2-data';
import { orderData } from './datasource';


class App extends React.Component<{}, {}> {
  public pageSettings: PageSettingsModel = { pageSize: 10 }
  public data: object[] = new DataManager(orderData).executeLocal(new Query().take(100));
  private grid: Grid | GridComponent | null;
  public chart: Chart | ChartComponent | null;
  public primaryxAxis: AxisModel = { valueType: 'DateTime' };
  public actionComplete(args: any) {
    if (args.requestType === 'paging') {
      (this.chart as Chart).series[0].dataSource = (this.grid as Grid).getCurrentViewRecords();
      (this.chart as Chart).refresh();
    }
  };
  public dataBound(args: any): void {
    (this.chart as Chart).series[0].dataSource = this.grid.getCurrentViewRecords();
  };
  render() {
    return (<div className='row'>
      <div className="col-sm-4" style={{ width: "400px", height: "350px", float: "left" }}>
        <GridComponent ref={g => this.grid = g} id='grid' dataSource={this.data} allowPaging={true} pageSettings={this.pageSettings} actionComplete={this.actionComplete.bind(this)} dataBound={this.dataBound.bind(this)}>
          <ColumnsDirective>
            <ColumnDirective field='OrderDate' headerText='Order Date' width='130' format='yMd' textAlign="Right" />
            <ColumnDirective field='Freight' width='120' format='C2' textAlign='Right' />
          </ColumnsDirective>
          <Inject services={[Page, Selection]} />
        </GridComponent>
      </div>
      <div className="col-sm-4" style={{ width: "400px", height: "400px", float: "left" }}>
        <ChartComponent ref={g => this.chart = g} id='chart' primaryXAxis={this.primaryxAxis}>
          <Inject services={[ColumnSeries, DateTime]} />
          <SeriesCollectionDirective>
            <SeriesDirective name='Germany' xName='OrderDate' yName='Freight' width={2} type='Column' marker={{ visible: true, width: 10, height: 10 }}>
            </SeriesDirective>
          </SeriesCollectionDirective>
        </ChartComponent>
      </div>
    </div>)
  }
};
ReactDOM.render(<App />, document.getElementById('charts'));
```

{% endtab %}