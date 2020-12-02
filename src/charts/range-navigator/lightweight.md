---
title: " RangeNavigator Lightweight | React "

component: "RangeNavigator"

description: "Lightweight rangenavigator is getting intialized when the datasource for series property is empty."
---

# Lightweight range navigator

By default, when the dataSource for series property in RangeNavigator is empty, a light weight Range navigator will get
initialized without chart. The following code example shows the basic lightweight range navigator.

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

  public data: object[] = GetDateTimeData(new Date(2018, 0, 1), new Date(2019, 0, 1));

  render() {
    return <RangeNavigatorComponent id='charts'
      valueType='DateTime' intervalType='Months' labelFormat='MMM'
      value={[new Date('2018-04-1'), new Date('2018-08-1')]} value={[new Date('2018-06-01'), new Date('2018-10-01')]}
      dataSource={this.data} xName='x' yName='y'>
      <Inject services={[DateTime]} />
    </RangeNavigatorComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));

```

{% endtab %}

## See Also

* [Period Selector](./period-selector/)