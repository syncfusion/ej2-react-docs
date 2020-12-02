---
title: " Bullet Chart Ranges | React "

component: "Bullet Chart"

description: "Bullet Chart scale can be rendered by using different types of end values. They are used to represnt the status of each data. "
---

# Ranges

`Ranges` are represents the quality of a specific range in bullet-chart scale like good, bad and satisfactory. The `end` property specifies the ending point of the qualitative range. `Minimum` value of quantitative scale is considered as the starting point of first range and previous end points are considered as starting point for other ranges.

## Color Customization

Color for each qualitative range is customized using `color` property based on end values. Also you can customize the opacity of the each range color.

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
                targetField='target'
                categoryField='category'
                categoryLabelStyle={{color:'red', size:'13', fontWeight:'bold'}}
                title='ales Rate'
                minimum={0}
                maximum={100}
                interval={10}
                dataSource={[{value: 55, target: 7.5, category: 'Year 1'},
                {value: 7, target: 5, category: 'Year 2'},
                {value: 10, target: 6, category: 'Year 3'}]}>
                <BulletRangeCollectionDirective>
                    <BulletRangeDirective end={35} color='darkred' opacity={0.5}></BulletRangeDirective>
                    <BulletRangeDirective end={50} color='red' opacity={1}></BulletRangeDirective>
                    <BulletRangeDirective end={75} color='blue' opacity={0.7}></BulletRangeDirective>
                    <BulletRangeDirective end={90} color='lightgreen' opacity={1}></BulletRangeDirective>
                    <BulletRangeDirective end={100} color='green' opacity={1}></BulletRangeDirective>
                </BulletRangeCollectionDirective>

            </BulletChartComponent>);
  }
};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}