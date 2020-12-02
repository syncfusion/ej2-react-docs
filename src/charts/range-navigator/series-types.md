---
title: " RangeNavigator Series Types | React "

component: "RangeNavigator"

description: "Essential JS 2 Range navigator supports 3 types of series, to render the data."
---

# Series Types

Essential JS 2 Range navigator supports 3 types of series, to render the data.

<!-- markdownlint-disable MD036 -->

## Line

<!-- markdownlint-disable MD036 -->

To render a line series, set the series[`type`](../api/range-navigator/rangeNavigatorSeries/#type) to `Line`, and
inject the `LineSeries` module using the `RangeNavigator.Inject(LineSeries)` method.

{% tab template="rangenavigator/getting-started", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx

import {
     LineSeries, DateTime, Inject, RangeNavigatorComponent, RangenavigatorSeriesCollectionDirective,
     RangenavigatorSeriesDirective,RangeTooltip,RangeTooltipSettingsModel
} from '@syncfusion/ej2-react-charts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { bitCoinData } from 'default_data.ts';

class App extends React.Component<{}, {}> {

  public data: object[] = bitCoinData;
  public tooltip: RangeTooltipSettingsModel = { enable: true };

  render() {
    return <RangeNavigatorComponent id='charts'
      valueType='DateTime' labelFormat='MMM-yy' value={[new Date('2017-09-01'), new Date('2018-02-01')]}
      tooltip={this.tooltip}>
      <Inject services={[LineSeries, DateTime, RangeTooltip]} />
      <RangenavigatorSeriesCollectionDirective>
        <RangenavigatorSeriesDirective dataSource={this.data} xName='x' yName='y' type='Line' width={2} />
      </RangenavigatorSeriesCollectionDirective>
    </RangeNavigatorComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));

```

{% endtab %}

## Area

To render a step line series, use series [`type`](../api/range-navigator/rangeNavigatorSeries/#type) as `Area` and
inject `AreaSeries` module using `RangeNavigator.Inject(AreaSeries)` method.

{% tab template="rangenavigator/getting-started", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx

import {
     AreaSeries, DateTime, Inject, RangeNavigatorComponent, RangenavigatorSeriesCollectionDirective,
     RangenavigatorSeriesDirective,RangeTooltip,RangeTooltipSettingsModel
} from '@syncfusion/ej2-react-charts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { bitCoinData } from 'default_data.ts';

class App extends React.Component<{}, {}> {

  public data: object[] = bitCoinData;
  public tooltip: RangeTooltipSettingsModel = { enable: true };

  render() {
    return <RangeNavigatorComponent id='charts'
      valueType='DateTime' labelFormat='MMM-yy' value={[new Date('2017-09-01'), new Date('2018-02-01')]}
      tooltip={this.tooltip}>
      <Inject services={[AreaSeries, DateTime, RangeTooltip]} />
      <RangenavigatorSeriesCollectionDirective>
        <RangenavigatorSeriesDirective dataSource={this.data} xName='x' yName='y' type='Area' width={2} />
      </RangenavigatorSeriesCollectionDirective>
    </RangeNavigatorComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));

```

{% endtab %}

## StepLine

To render a step line series, use series [`type`](../api/range-navigator/rangeNavigatorSeries/#type) as `StepLine` and
inject `StepLineSeries` module using `RangeNavigator.Inject(StepLineSeries)` method.

{% tab template="rangenavigator/getting-started", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx

import {
     StepLineSeries, DateTime, Inject, RangeNavigatorComponent, RangenavigatorSeriesCollectionDirective,
     RangenavigatorSeriesDirective,RangeTooltip,RangeTooltipSettingsModel
} from '@syncfusion/ej2-react-charts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { double } from 'default_data.ts';

class App extends React.Component<{}, {}> {

  public data: object[] = double;
  public tooltip: RangeTooltipSettingsModel = { enable: true };

  render() {
    return <RangeNavigatorComponent id='charts'
      labelPosition='Outside'
      tooltip={this.tooltip}
      value={[12, 30]}>
      <Inject services={[RangeTooltip, StepLineSeries]} />
      <RangenavigatorSeriesCollectionDirective>
        <RangenavigatorSeriesDirective dataSource={this.data} xName='x' yName='y'>
        </RangenavigatorSeriesDirective>
      </RangenavigatorSeriesCollectionDirective>
    </RangeNavigatorComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}