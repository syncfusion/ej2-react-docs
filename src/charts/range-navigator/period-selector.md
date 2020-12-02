---
title: " RangeNavigator Period Selector | React "

component: "RangeNavigator"

description: "The period selector allows to select a range with specified periods."
---

# Period selector

The period selector allows to select a range with specified periods.

## Periods

Periods is an array of objects that allows users to specify the range of periods. The “interval” property specifies the count value of the button, and the “text” property specifies the text to be displayed on button. The “intervalType” property allows users to customize the intervals of the buttons. The “intervalType” property supports the following interval types:

* Auto
* Years
* Quarter
* Months
* Weeks
* Days
* Hours
* Minutes
* Seconds

{% tab template="rangenavigator/getting-started", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx

import {
     AreaSeries, DateTime, Inject, RangeNavigatorComponent, RangenavigatorSeriesCollectionDirective,
     RangenavigatorSeriesDirective,RangeTooltip, PeriodSelector, RangeTooltipSettingsModel, PeriodSelectorSettingsModel
} from '@syncfusion/ej2-react-charts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { bitCoinData } from 'default_data.ts';

class App extends React.Component<{}, {}> {

  public data: object[] = bitCoinData;
  public tooltip: RangeTooltipSettingsModel = { enable: true };
  public periodselector: PeriodSelectorSettingsModel = {
    position: 'Top',
    periods: [
      { text: '1M', interval: 1, intervalType: 'Months' },
      { text: '3M', interval: 3, intervalType: 'Months' },
      { text: '6M', interval: 6, intervalType: 'Months' }, { text: 'YTD' },
      { text: '1Y', interval: 1, intervalType: 'Years' },
      { text: '2Y', interval: 2, intervalType: 'Years', selected: true }, { text: 'All' }
    ]
  };

  render() {
    return <RangeNavigatorComponent id='charts'
      valueType='DateTime' labelFormat='MMM-yy' value={[new Date('2017-09-01'), new Date('2018-02-01')]}
      tooltip={this.tooltip}
      periodSelectorSettings={this.periodselector}>
      <Inject services={[AreaSeries, DateTime, RangeTooltip, PeriodSelector]} />
      <RangenavigatorSeriesCollectionDirective>
        <RangenavigatorSeriesDirective dataSource={this.data} xName='x' yName='y' type='Area' width={2} />
      </RangenavigatorSeriesCollectionDirective>
    </RangeNavigatorComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));

```

{% endtab %}

>Note: To use the period selector feature, inject the PeriodSelector module using the RangeNavigator.Inject(PeriodSelector)
method.

## Positioning period selector

The “position” property allows users to position the period selector either at the “top” or “bottom”.

{% tab template="rangenavigator/getting-started", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx

import {
     AreaSeries, DateTime, Inject, RangeNavigatorComponent, RangenavigatorSeriesCollectionDirective,
     RangenavigatorSeriesDirective,RangeTooltip, PeriodSelector,RangeTooltipSettingsModel, PeriodSelectorSettingsModel
} from '@syncfusion/ej2-react-charts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { bitCoinData } from 'default_data.ts';

class App extends React.Component<{}, {}> {

  public data: object[] = bitCoinData;
  public tooltip: RangeTooltipSettingsModel = { enable: true };
  public periodselector: PeriodSelectorSettingsModel = {
    position: 'Bottom',
    periods: [
      { text: '1M', interval: 1, intervalType: 'Months' },
      { text: '3M', interval: 3, intervalType: 'Months' },
      { text: '6M', interval: 6, intervalType: 'Months' }, { text: 'YTD' },
      { text: '1Y', interval: 1, intervalType: 'Years' },
      { text: '2Y', interval: 2, intervalType: 'Years', selected: true }, { text: 'All' }
    ]
  };

  render() {
    return <RangeNavigatorComponent id='charts'
      valueType='DateTime' labelFormat='MMM-yy' value={[new Date('2017-09-01'), new Date('2018-02-01')]}
      tooltip={this.tooltip}
      periodSelectorSettings={this.periodselector}>
      <Inject services={[AreaSeries, DateTime, RangeTooltip, PeriodSelector]} />
      <RangenavigatorSeriesCollectionDirective>
        <RangenavigatorSeriesDirective dataSource={this.data} xName='x' yName='y' type='Area' width={2} />
      </RangenavigatorSeriesCollectionDirective>
    </RangeNavigatorComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));

```

{% endtab %}

## Height

The “height” property allows users to specify the height for period selector. The default value of the height property is 43.

{% tab template="rangenavigator/getting-started", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx

import {
     AreaSeries, DateTime, Inject, RangeNavigatorComponent, RangenavigatorSeriesCollectionDirective,
     RangenavigatorSeriesDirective,RangeTooltip, PeriodSelector,RangeTooltipSettingsModel, PeriodSelectorSettingsModel
} from '@syncfusion/ej2-react-charts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { bitCoinData } from 'default_data.ts';

class App extends React.Component<{}, {}> {

  public data: object[] = bitCoinData;
  public tooltip: RangeTooltipSettingsModel = { enable: true };
  public periodselector: PeriodSelectorSettingsModel = {
    position: 'Top',
    height: 65,
    periods: [
      { text: '1M', interval: 1, intervalType: 'Months' },
      { text: '3M', interval: 3, intervalType: 'Months' },
      { text: '6M', interval: 6, intervalType: 'Months' }, { text: 'YTD' },
      { text: '1Y', interval: 1, intervalType: 'Years' },
      { text: '2Y', interval: 2, intervalType: 'Years', selected: true }, { text: 'All' }
    ]
  };

  render() {
    return <RangeNavigatorComponent id='charts'
      valueType='DateTime' labelFormat='MMM-yy' value={[new Date('2017-09-01'), new Date('2018-02-01')]}
      tooltip={this.tooltip}
      periodSelectorSettings={this.periodselector}>
      <Inject services={[AreaSeries, DateTime, RangeTooltip, PeriodSelector]} />
      <RangenavigatorSeriesCollectionDirective>
        <RangenavigatorSeriesDirective dataSource={this.data} xName='x' yName='y' type='Area' width={2} />
      </RangenavigatorSeriesCollectionDirective>
    </RangeNavigatorComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));

```

{% endtab %}

## Visibility of range navigator

The “disableRangeSelector” property allows users to render the period selector without range navigator.

{% tab template="rangenavigator/getting-started", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx

import {
     AreaSeries, DateTime, Inject, RangeNavigatorComponent, RangenavigatorSeriesCollectionDirective,
     RangenavigatorSeriesDirective,RangeTooltip, PeriodSelector,RangeTooltipSettingsModel, PeriodSelectorSettingsModel
} from '@syncfusion/ej2-react-charts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { bitCoinData } from 'default_data.ts';

class App extends React.Component<{}, {}> {

  public data: object[] = bitCoinData;
  public tooltip: RangeTooltipSettingsModel = { enable: true };
  public periodselector: PeriodSelectorSettingsModel = {
    position: 'Top',
    periods: [
      { text: '1M', interval: 1, intervalType: 'Months' },
      { text: '3M', interval: 3, intervalType: 'Months' },
      { text: '6M', interval: 6, intervalType: 'Months' }, { text: 'YTD' },
      { text: '1Y', interval: 1, intervalType: 'Years' },
      { text: '2Y', interval: 2, intervalType: 'Years', selected: true }, { text: 'All' }
    ]
  };

  render() {
    return <RangeNavigatorComponent id='charts'
      valueType='DateTime' labelFormat='MMM-yy' value={[new Date('2017-09-01'), new Date('2018-02-01')]}
      dataSource={this.data} xName='x' yName='y'
      disableRangeSelector={true}
      tooltip={this.tooltip}
      periodSelectorSettings={this.periodselector}>
      <Inject services={[AreaSeries, DateTime, RangeTooltip, PeriodSelector]} />
    </RangeNavigatorComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));

```

{% endtab %}

## See Also

* [LightWeight](./lightweight/)