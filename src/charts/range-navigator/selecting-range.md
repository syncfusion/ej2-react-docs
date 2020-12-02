---
title: " RangeNavigator Selecting Range | React "

component: "RangeNavigator"

description: "we can able to select the particular range data by dragging thumbs or by tapping on the labels or by setting the start and end value properties. "
---

# Selecting Range

The left and right thumb of RangeNavigator are used to indicate the selected range in the large collection of data. Following are the ways you can select a range.

* By dragging the thumbs.
* By tapping on the labels.
* By setting the start and end through value properties.

Following code example shows how to configure the selected range using value  property of RangeNavigator.

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
