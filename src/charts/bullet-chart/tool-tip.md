---
title: "BulletChart Tooltip | React "

component: "BulletChart"

description: "Tooltip is used to show the data value when mouse hover on the chart.We can able to customize format,template and appearance."
---

# Tooltip

BulletChart will display details about the actual and target values through tooltip, when the mouse is moved over the target and feature bar.

## Default Tooltip

By setting [`enable`](https://ej2.syncfusion.com/documentation/api/bullet-chart/bulletTooltipSettingsModel/#enable)property to true. By default tooltip is visible in bullet-chart.

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
                        tooltip={{enable: true}}
                        dataSource={[{value: 5, comparativeMeasureValue: 7.5, category: '2001'},
                        {value: 7, comparativeMeasureValue: 5, category: '2002'},
                        {value: 10, comparativeMeasureValue: 6, category: '2003'},
                        {value: 5, comparativeMeasureValue: 8, category: '2004'},
                        {value: 12, comparativeMeasureValue: 5, category: '2005'},
                        {value: 8, comparativeMeasureValue: 6, category: '2006'},]}>
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

## Tooltip Template

Any HTML elements can be displayed in the tooltip by using the `template` property of the tooltip. You can use the ${target} and ${value} as place holders in the HTML element to display the value and target values of the corresponding data point.

## Customize the Appearance of Tooltip

The [`fill`](./https://ej2.syncfusion.com/documentation/api/bullet-chart/bulletTooltipSettingsModel/#fill) and [`border`](./https://ej2.syncfusion.com/documentation/api/bullet-chart/bulletTooltipSettingsModel/#border) properties are used to customize the background color and border of the tooltip respectively. The [`textStyle`](./https://ej2.syncfusion.com/documentation/api/bullet-chart/bulletTooltipSettingsModel/#textstyle) property in the tooltip is used to customize the font of the tooltip text.