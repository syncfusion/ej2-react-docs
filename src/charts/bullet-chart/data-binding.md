---
title: " Bullet Chart DataBinding | React "

component: "Bullet Chart"

description: "Bullet Chart can be rendered by using different types of data source. They are called local data, remote data. "
---

# Working with Data

Bullet Chart can visualise data bound from local or remote data.

## Local Data

You can bind a simple JSON data to the chart using
[`dataSource`](../api/bullet-chart/) direct property of the bullet-chart. Now map the fields in
JSON to [`valueField`](../api/bullet-chart/#valueField-string) and [`targetField`](../api/bullet-chart/#targetField-string) properties.

{% tab template="bullet-chart/working-with-data/local-data", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import { BulletChartComponent, Inject} from '@syncfusion/ej2-react-charts';
import { BulletRangeCollectionDirective, BulletRangeDirective} from '@syncfusion/ej2-react-charts';
import * as React from "react";
import * as ReactDOM from "react-dom";

class App extends React.Component<{}, {}>{
  render() {
    return (<BulletChartComponent id='ranges'
                        animation={{ enable: false }}
                        height="400"
                        valueField='value'
                        targetField='comparativeMeasureValue'
                        categoryField='category'
                        title='Profit in %'
                        minimum={0}
                        maximum={20}
                        interval={5}
                        dataSource={[{value: 5, comparativeMeasureValue: 7.5, category: '2001'},
                        {value: 7, comparativeMeasureValue: 5, category: '2002'},
                        {value: 10, comparativeMeasureValue: 6, category: '2003'},
                        {value: 5, comparativeMeasureValue: 8, category: '2004'},
                        {value: 12, comparativeMeasureValue: 5, category: '2005'},
                        {value: 8, comparativeMeasureValue: 6, category: '2006'}]}>
                        <BulletRangeCollectionDirective>
                            <BulletRangeDirective end={5} ></BulletRangeDirective>
                            <BulletRangeDirective end={15}></BulletRangeDirective>
                            <BulletRangeDirective end={20}></BulletRangeDirective>
                        </BulletRangeCollectionDirective>

            </BulletChartComponent>);
  }
};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}