---
title: " RangeNavigator Labels | React "

component: "RangeNavigator"

description: "RangeNavigator supports Multilevel label and enable grouping properties to customize axis labels."
---

# Labels

## Multilevel labels

The second level labels for the range navigator can be enabled by setting the “enableGrouping” property to true.
This is restricted to date-time axis alone.

{% tab template="rangenavigator/lightweight", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx

import {
     AreaSeries, DateTime, Inject, RangeNavigatorComponent, RangenavigatorSeriesCollectionDirective,
     RangenavigatorSeriesDirective,RangeTooltip
} from '@syncfusion/ej2-react-charts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { GetDateTimeData } from 'default_data.ts';

class App extends React.Component<{}, {}> {

  public data: object[] = [];
  public chartLoad(): void {
    let value: number = 0; let point: object = {};
    for (let j: number = 1; j < 1090; j++) {
      value += (Math.random() * 10 - 5);
      value = value < 0 ? Math.abs(value) : value;
      point = { x: new Date(2000, 0, j), y: value, z: value + 10 };
      this.data.push(point);
    }
  }

  render() {
    this.chartLoad();
    return <RangeNavigatorComponent id='charts'
      valueType='DateTime' intervalType='Months'
      intervalType='Quarter' enableGrouping={true}
      value={[new Date('2001-01-01'), new Date('2002-01-01')]}
      dataSource={this.data} xName='x' yName='y'>
      <Inject services={[DateTime]} />
    </RangeNavigatorComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

## Grouping

The second level axis labels can be grouped using “groupBy” property with the following interval types:

* Auto
* Years
* Quarter
* Months
* Weeks
* Days
* Hours
* Minutes
* Seconds

{% tab template="rangenavigator/lightweight", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx

import {
     AreaSeries, DateTime, Inject, RangeNavigatorComponent, RangenavigatorSeriesCollectionDirective,
     RangenavigatorSeriesDirective,RangeTooltip
} from '@syncfusion/ej2-react-charts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { GetDateTimeData } from 'default_data.ts';

class App extends React.Component<{}, {}> {

  public data: object[] = [];
  public chartLoad(): void {
    let value: number = 0; let point: object = {};
    for (let j: number = 1; j < 1090; j++) {
      value += (Math.random() * 10 - 5);
      value = value < 0 ? Math.abs(value) : value;
      point = { x: new Date(2000, 0, j), y: value, z: value + 10 };
      this.data.push(point);
    }
  }

  render() {
    this.chartLoad();
    return <RangeNavigatorComponent id='charts'
      valueType='DateTime' intervalType='Months'
      intervalType='Quarter'
      enableGrouping={true}
      groupBy='Years'
      value={[new Date('2001-01-01'), new Date('2002-01-01')]}
      dataSource={this.data} xName='x' yName='y'>
      <Inject services={[DateTime]} />
    </RangeNavigatorComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

## Smart labels

The “labelIntersectAction” property is used to avoid overlapping of labels.

The following code sample shows setting the labelIntersectAction property to Hide.

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
      valueType='DateTime' labelFormat='y/M/d' value={[new Date('2017-09-01'), new Date('2018-02-01')]}
      tooltip={this.tooltip} labelIntersectAction='Hide'>
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

## Label positioning

By default, the labels can be placed at outside of the range navigator. You can place the labels inside the range navigator
using the labelPosition property.

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
      valueType='DateTime' labelPosition='Inside' value={[new Date('2017-09-01'), new Date('2018-02-01')]}
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

## Labels customization

The font size, color, family, etc. can be customized using the “labelStyle” property.

{% tab template="rangenavigator/lightweight", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx

import {
     AreaSeries, DateTime, Inject, RangeNavigatorComponent, RangenavigatorSeriesCollectionDirective,
     RangenavigatorSeriesDirective,RangeTooltip
} from '@syncfusion/ej2-react-charts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { GetDateTimeData } from 'default_data.ts';

class App extends React.Component<{}, {}> {

  public data: object[] = [];
  public max: number = 100;
  public chartLoad(): void {
    let value: number = 0; let point: object = {};
    for (let j: number = 1; j < 1090; j++) {
      value += (Math.random() * 10 - 5);
      value = value < 0 ? Math.abs(value) : value;
      point = { x: new Date(2000, 0, j), y: value, z: value + 10 };
      this.data.push(point);
    }
  }

  render() {
    this.chartLoad();
    return <RangeNavigatorComponent id='charts'
      valueType='DateTime' intervalType='Months' labelFormat='MMM'
      value={[new Date('2001-01-01'), new Date('2002-01-01')]}
      dataSource={this.data} xName='x' yName='y'>
      <Inject services={[DateTime]} />
    </RangeNavigatorComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}