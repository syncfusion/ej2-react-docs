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

{% tab template="chart/grid-visual", sourceFiles="app/**/*.tsx" %}

```typescript
import * as React from "react";
import * as ReactDOM from "react-dom";
import {
  ChartComponent, SeriesCollectionDirective, SeriesDirective, Inject, AxisModel, Chart, ColumnSeries, DateTime
} from '@syncfusion/ej2-react-charts';
import { ColumnDirective, ColumnsDirective, GridComponent, Page, PageSettingsModel, Selection, Grid } from '@syncfusion/ej2-react-grids';
class App extends React.Component<{}, {}> {
  public pageSettings: PageSettingsModel = { pageSize: 10 }
  public grid: Grid | null;
  public chart: Chart | null;
  public primaryxAxis: AxisModel = { valueType: 'DateTime' };
  public actionComplete(args: any) {
    if (args.requestType === 'paging') {
      (this.chart as Chart).series[0].dataSource = (this.grid as Grid).getCurrentViewRecords();
      (this.chart as Chart).refresh();
    }
  };
  public dataBound(args: any): void {
    (this.chart as Chart).series[0].dataSource = (this.grid as Grid).getCurrentViewRecords();
  };
  public data: any[] = [
    {
        'OrderDate': '1996-07-06',
        'ShippedDate': '1996-07-16',
        'Freight': 32.38
    },
    {
        'OrderDate': '1996-07-07',
        'ShippedDate': '1996-07-10',
        'Freight': 11.61
    },
    {
        'OrderDate': '1996-07-08',
        'ShippedDate': '1996-07-12',
        'Freight': 65.83
    },
    {
        'OrderDate': '1996-07-09',
        'ShippedDate': '1996-07-15',
        'Freight': 41.34
    },
    {
        'OrderDate': '1996-07-10',
        'ShippedDate': '1996-07-11',
        'Freight': 51.3
    },
    {
        'OrderDate': '1996-07-11',
        'ShippedDate': '1996-07-16',
        'Freight': 58.17
    },
    {
        'OrderDate': '1996-07-12',
        'ShippedDate': '1996-07-23',
        'Freight': 22.98
    },
    {
        'OrderDate': '1996-07-13',
        'ShippedDate': '1996-07-15',
        'Freight': 148.33
    },
    {
        'OrderDate': '1996-07-14',
        'ShippedDate': '1996-07-17',
        'Freight': 13.97
    },
    {
        'OrderDate': '1996-07-15',
        'ShippedDate': '1996-07-22',
        'Freight': 81.91
    },
    {
        'OrderDate': '1996-07-16',
        'ShippedDate': '1996-07-23',
        'Freight': 140.51
    },
    {
        'OrderDate': '1996-07-17',
        'ShippedDate': '1996-07-25',
        'Freight': 3.25
    },
    {
        'OrderDate': '1996-07-18',
        'ShippedDate': '1996-07-29',
        'Freight': 55.09
    },
    {
        'OrderDate': '1996-07-19',
        'ShippedDate': '1996-07-30',
        'Freight': 3.05
    },
    {
        'OrderDate': '1996-07-20',
        'ShippedDate': '1996-07-25',
        'Freight': 48.29
    },
    {
        'OrderDate': '1996-07-21',
        'ShippedDate': '1996-07-31',
        'Freight': 146.06
    },
    {
        'OrderDate': '1996-07-22',
        'ShippedDate': '1996-08-23',
        'Freight': 3.67
    },
    {
        'OrderDate': '1996-07-23',
        'ShippedDate': '1996-08-12',
        'Freight': 55.28
    },
    {
        'OrderDate': '1996-07-24',
        'ShippedDate': '1996-07-31',
        'Freight': 25.73
    },
    {
        'OrderDate': '1996-07-25',
        'ShippedDate': '1996-08-06',
        'Freight': 208.58
    },
    {
        'OrderDate': '1996-07-26',
        'ShippedDate': '1996-08-02',
        'Freight': 66.29
    },
    {
        'OrderDate': '1996-07-27',
        'ShippedDate': '1996-08-09',
        'Freight': 4.56
    },
    {
        'OrderDate': '1996-07-29',
        'ShippedDate': '1996-08-02',
        'Freight': 136.54
    },
    {
        'OrderDate': '1996-07-30',
        'ShippedDate': '1996-08-30',
        'Freight': 4.54
    },
    {
        'OrderDate': '1996-07-31',
        'ShippedDate': '1996-08-06',
        'Freight': 98.03
    },
    {
        'OrderDate': '1996-08-01',
        'ShippedDate': '1996-08-12',
        'Freight': 76.07
    },
    {
        'OrderDate': '1996-08-02',
        'ShippedDate': '1996-08-16',
        'Freight': 6.01
    },
    {
        'OrderDate': '1996-08-03',
        'ShippedDate': '1996-08-09',
        'Freight': 26.93
    },
    {
        'OrderDate': '1996-08-04',
        'ShippedDate': '1996-08-14',
        'Freight': 13.84
    },
    {
        'OrderDate': '1996-08-05',
        'ShippedDate': '1996-08-13',
        'Freight': 125.77
    },
    {
        'OrderDate': '1996-08-06',
        'ShippedDate': '1996-08-16',
        'Freight': 92.69
    },
    {
        'OrderDate': '1996-08-07',
        'ShippedDate': '1996-08-16',
        'Freight': 25.83
    },
    {
        'OrderDate': '1996-08-08',
        'ShippedDate': '1996-09-12',
        'Freight': 8.98
    },
    {
        'OrderDate': '1996-08-09',
        'ShippedDate': '1996-08-21',
        'Freight': 2.94
    },
    {
        'OrderDate': '1996-08-10',
        'ShippedDate': '1996-08-21',
        'Freight': 12.69
    },
    {
        'OrderDate': '1996-08-11',
        'ShippedDate': '1996-08-28',
        'Freight': 12.76
    },
    {
        'OrderDate': '1996-08-12',
        'ShippedDate': '1996-09-03',
        'Freight': 7.45
    },
    {
        'OrderDate': '1996-08-13',
        'ShippedDate': '1996-08-28',
        'Freight': 22.77
    },
    {
        'OrderDate': '1996-08-14',
        'ShippedDate': '1996-09-03',
        'Freight': 79.7
    },
    {
        'OrderDate': '1996-08-15',
        'ShippedDate': '1996-09-04',
        'Freight': 6.4
    }];
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
        <ChartComponent ref={g => this.chart = g} id='charts' primaryXAxis={this.primaryxAxis}>
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