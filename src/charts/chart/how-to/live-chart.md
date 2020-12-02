---
title: " Chart How To | React "

component: "Chart"

description: "How to section explains knowledge base samples and howto access different types properties and events of the chart."
---

# Create a live chart

You can update a chart with live data by using the set interval.

To update live data in a chart, follow the given steps:

**Step 1**:

Initialize the chart with series.

**Step 2**:

Update the data to series, and refresh the chart at specified interval by using the set interval.

To refresh the chart, invoke the `refresh` method.

{% tab template="chart/how-to", sourceFiles="app/**/*.tsx" %}

```typescript
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { ChartComponent, SeriesCollectionDirective, SeriesDirective, Inject,
         Legend, Category, Tooltip, DataLabel, LineSeries, ILoadedEventArgs}
from'@syncfusion/ej2-react-charts';
import { getElement } from '@syncfusion/ej2-charts';

class App extends React.Component<{}, {}>{

  private chart: ChartComponent;
  public series1: Object[] = [];
  public value: number = 10;
  public intervalId: any;
  public setTimeoutValue: number;
  public i: number = 0;
  public loaded(args: ILoadedEventArgs): void {
    this.setTimeoutValue = 100;
    this.intervalId = setInterval(
      () => {
        let i: number;
        if (getElement('charts') === null) {
          clearInterval(this.intervalId);
        } else {
          if (Math.random() > .5) {
            if (this.value < 25) {
              this.value += Math.random() * 2.0;
            } else {
              this.value -= 2.0;
            }
          }
          this.i++;
          this.series1.push({ x: this.i, y: this.value });
          this.series1.shift();
          args.chart.series[0].dataSource = this.series1;
          args.chart.refresh();
        }
      },
      this.setTimeoutValue);
  }
  constructor() {
    super()
    for (; this.i < 100; this.i++) {
      if (Math.random() > .5) {
        if (this.value < 25) {
          this.value += Math.random() * 2.0;
        } else {
          this.value -= 2.0;
        }
      }
      this.series1[this.i] = { x: this.i, y: this.value };

    }
  };

  render() {
    return <ChartComponent id='charts'
      primaryXAxis={{ majorGridLines: { width: 0 } }}
      primaryYAxis={{ minimum: 0, maximum: 50 }}
      loaded={this.loaded.bind(this)}>
      <Inject services={[LineSeries]} />
      <SeriesCollectionDirective>
        <SeriesDirective dataSource={this.series1} xName='x' yName='y' type='Line'>
        </SeriesDirective>
      </SeriesCollectionDirective>
    </ChartComponent>
  }

};
ReactDOM.render(<App />, document.getElementById('charts'));
```

{% endtab %}