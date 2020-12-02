---
title: " RangeNavigator Grid and Tick lines | React "

component: "RangeNavigator"

description: "RangeNavigator supports customization of width, color, and dashArray of the major grid lines using the majorGridLines property."
---

# Grid and Tick Lines

## Grid line customization

You can customize the width, color, and dashArray of the major grid lines using the majorGridLines property.

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

  public data: object[] = [
    { xData: 10, yData: 35 }, { xData: 20, yData: 28 },
    { xData: 30, yData: 34 }, { xData: 40, yData: 32 },
    { xData: 50, yData: 40 }
  ];
  public tooltip: RangeTooltipSettingsModel = { enable: true };
  public majorgridLines = { width: 4, color: 'blue', dashArray: '5,5' };

  render() {
    return <RangeNavigatorComponent id='charts'
      labelPosition='Outside'
      tooltip={this.tooltip}
      majorGridLines={this.majorgridLines}
      value={[25, 40]}>
      <Inject services={[RangeTooltip, StepLineSeries]} />
      <RangenavigatorSeriesCollectionDirective>
        <RangenavigatorSeriesDirective dataSource={this.data} xName='xData' yName='yData'>
        </RangenavigatorSeriesDirective>
      </RangenavigatorSeriesCollectionDirective>
    </RangeNavigatorComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));

```

{% endtab %}

## Tick line customization

You can customize the width, color, and height of the major tick lines using the majorTickLines property.

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

  public data: object[] = [
    { xData: 10, yData: 35 }, { xData: 20, yData: 28 },
    { xData: 30, yData: 34 }, { xData: 40, yData: 32 },
    { xData: 50, yData: 40 }
  ];
  public tooltip: RangeTooltipSettingsModel = { enable: true };
  public majortickLines = { width: 3, color: 'red' };

  render() {
    return <RangeNavigatorComponent id='charts'
      labelPosition='Outside'
      tooltip={this.tooltip}
      majorTickLines={this.majortickLines}
      value={[25, 40]}>
      <Inject services={[RangeTooltip, StepLineSeries]} />
      <RangenavigatorSeriesCollectionDirective>
        <RangenavigatorSeriesDirective dataSource={this.data} xName='xData' yName='yData'>
        </RangenavigatorSeriesDirective>
      </RangenavigatorSeriesCollectionDirective>
    </RangeNavigatorComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));

```

{% endtab %}