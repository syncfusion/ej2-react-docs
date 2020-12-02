---
title: " Chart Print and Export | React "

component: "Chart"

description: "The rendered chart can be printed or exported directly from the browser by calling the public method print and export."
---

# Print and export

## Print

The rendered chart can be printed directly from the browser by calling the public method print.
From chart instance itself, it is called.

{% tab template= "chart/print", compileJsx=true %}

```tsx

import * as React from "react";
import * as ReactDOM from "react-dom";
import { AxisModel, ChartComponent, SeriesCollectionDirective, AxesDirective, AxisDirective, SeriesDirective, Inject,
ColumnSeries, Legend, Category, Tooltip, DataLabel, Zoom, Crosshair, LineSeries,  Selection}
from'@syncfusion/ej2-react-charts';

class App extends React.Component<{}, {}>{

  public data: any[] = [
    { month: 'Jan', sales: 35 }, { month: 'Feb', sales: 28 },
    { month: 'Mar', sales: 34 }, { month: 'Apr', sales: 32 },
    { month: 'May', sales: 40 }, { month: 'Jun', sales: 32 },
    { month: 'Jul', sales: 35 }, { month: 'Aug', sales: 55 },
    { month: 'Sep', sales: 38 }, { month: 'Oct', sales: 30 },
    { month: 'Nov', sales: 25 }, { month: 'Dec', sales: 32 }
  ];
  public chartInstance: ChartComponent;
  public clickHandler() {
    this.chartInstance.print();
  }
  public primaryxAxis: AxisModel = { valueType: 'Category' };

  render() {
    return (<div>
      <button value='print' onClick={this.clickHandler.bind(this)}>Print</button>
      <ChartComponent id='charts' ref={chart => this.chartInstance = chart} primaryXAxis={this.primaryxAxis}>
        <Inject services={[ColumnSeries, Legend, Tooltip, DataLabel, LineSeries, Category]} />
        <SeriesCollectionDirective>
          <SeriesDirective dataSource={this.data} xName='month' yName='sales' type='Column' name='Sales'>
          </SeriesDirective>
        </SeriesCollectionDirective>
      </ChartComponent></div>)
  }

};
ReactDOM.render(<App />, document.getElementById('charts'));
```

{% endtab %}

## Export

The rendered chart can be exported to `JPEG` , `PNG`, `SVG`or `PDF` format by using export method in chart.
Input parameters for this method are `Export Type` for format and `fileName` of result.

{% tab template= "chart/print", compileJsx=true %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { ChartComponent, SeriesCollectionDirective, AxesDirective, AxisDirective, SeriesDirective, Inject,AxisModel,
ColumnSeries, Export, Legend, Category, Tooltip, DataLabel, Zoom, Crosshair, LineSeries,  Selection}
from'@syncfusion/ej2-react-charts';

class App extends React.Component<{}, {}>{

  public data: any[] = [
    { month: 'Jan', sales: 35 }, { month: 'Feb', sales: 28 },
    { month: 'Mar', sales: 34 }, { month: 'Apr', sales: 32 },
    { month: 'May', sales: 40 }, { month: 'Jun', sales: 32 },
    { month: 'Jul', sales: 35 }, { month: 'Aug', sales: 55 },
    { month: 'Sep', sales: 38 }, { month: 'Oct', sales: 30 },
    { month: 'Nov', sales: 25 }, { month: 'Dec', sales: 32 }
  ];
  public chartInstance: ChartComponent;
  public clickHandler() {
    this.chartInstance.exportModule.export('PNG', 'sample');
  }
  public primaryxAxis: AxisModel = { valueType: 'Category' };

  render() {
    return (<div><button value='print' onClick={this.clickHandler.bind(this)}>Export</button>
      <ChartComponent id='charts' ref={chart => this.chartInstance = chart} primaryXAxis={this.primaryxAxis}>
        <Inject services={[ColumnSeries, Legend, Tooltip, DataLabel,Export, LineSeries, Category]} />
        <SeriesCollectionDirective>
          <SeriesDirective dataSource={this.data} xName='month' yName='sales' type='Column' name='Sales'>
          </SeriesDirective>
        </SeriesCollectionDirective>
      </ChartComponent></div>)
  }

};
ReactDOM.render(<App />, document.getElementById('charts'));

```

{% endtab %}