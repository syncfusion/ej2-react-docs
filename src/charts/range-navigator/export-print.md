---
title: " RangeNavigator Export and Print | React "

component: "RangeNavigator"

description: "The rendered rangenavigator can be printed or exported directly from the browser by calling the public method print and export."
---

# Export and print

## Export

The rendered range navigator can be exported to JPEG, PNG, SVG, or PDF format using the export method in the range navigator. The input parameters for this method are Export Type for format and fileName for result.

{% tab template="rangenavigator/export", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx

import {
     AreaSeries, DateTime, Inject, RangeNavigatorComponent, RangenavigatorSeriesCollectionDirective,
     RangenavigatorSeriesDirective,RangeTooltip, RangeNavigator,RangeTooltipSettingsModel
} from '@syncfusion/ej2-react-charts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { bitCoinData } from 'default_data.ts';

class App extends React.Component<{}, {}>{

  public data: object[] = bitCoinData;
  public tooltip: RangeTooltipSettingsModel = { enable: true };
  public clickHandler() {
    this.range.export('PNG', 'sample');
  }
  private range: RangeNavigator;

  render() {
    return (<div>
      <ButtonComponent value='export' onClick={this.clickHandler.bind(this)}>Export</ButtonComponent>
      <RangeNavigatorComponent id='charts' ref={g => this.range = g}
        valueType='DateTime' labelFormat='MMM-yy' value={[new Date('2017-09-01'), new Date('2018-02-01')]}
        tooltip={this.tooltip}>
        <Inject services={[AreaSeries, DateTime, RangeTooltip]} />
        <RangenavigatorSeriesCollectionDirective>
          <RangenavigatorSeriesDirective dataSource={this.data} xName='x' yName='y' type='Area' width={2} />
        </RangenavigatorSeriesCollectionDirective>
      </RangeNavigatorComponent></div>)
  }

};
ReactDOM.render(<App />, document.getElementById('charts'));

```

{% endtab %}

## Print

The rendered range navigator can be printed directly from the browser by calling the public method print. The ID of the range navigator div element must be passed as argument to that method.

{% tab template="rangenavigator/print", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx

import {
     AreaSeries, DateTime, Inject, RangeNavigatorComponent, RangenavigatorSeriesCollectionDirective,
     RangenavigatorSeriesDirective,RangeTooltip, RangeNavigator,RangeTooltipSettingsModel
} from '@syncfusion/ej2-react-charts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { ButtonComponent } from '@syncfusion/ej2-react-buttons';
import { bitCoinData } from 'default_data.ts';

class App extends React.Component<{}, {}>{

  public data: object[] = bitCoinData;
  public tooltip: RangeTooltipSettingsModel = { enable: true };
  public clickHandler() {
    this.range.print();
  }
  private range: RangeNavigator;

  render() {
    return (<div> <ButtonComponent value='print' onClick={this.clickHandler.bind(this)}>Print</ButtonComponent>
      <RangeNavigatorComponent id='charts' ref={g => this.range = g}
        valueType='DateTime' labelFormat='MMM-yy' value={[new Date('2017-09-01'), new Date('2018-02-01')]}
        tooltip={this.tooltip}>
        <Inject services={[AreaSeries, DateTime, RangeTooltip]} />
        <RangenavigatorSeriesCollectionDirective>
          <RangenavigatorSeriesDirective dataSource={this.data} xName='x' yName='y' type='Area' width={2} />
        </RangenavigatorSeriesCollectionDirective>
      </RangeNavigatorComponent></div>)
  }

};
ReactDOM.render(<App />, document.getElementById('charts'));
```

{% endtab %}
