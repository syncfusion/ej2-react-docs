---
title: " Bullet Chart Value Bar | React "

component: "Bullet Chart"

description: "The main data value is encoded by a length of the main bar in the middle of the chart, known as the Feature Measure. "
---

# Feature Bar

The main data value is encoded by a length of the main bar in the middle of the chart, known as the `Feature Measure`. This is also called as `value Bar`. Also, if you want to display the target bar you should map the `valueField` name from the dataSource.

{% tab template="bullet-chart/value-bar", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import { BulletChartComponent, Inject} from '@syncfusion/ej2-react-charts';
import { BulletRangeCollectionDirective, BulletRangeDirective} from '@syncfusion/ej2-react-charts';
import * as React from "react";
import * as ReactDOM from "react-dom";

class App extends React.Component<{}, {}>{
  render() {
    return (<BulletChartComponent id='ranges'
                animation={{ enable: false }}
                        valueField='value'
                        targetField='target'
                        title='Sales Rate'
                        minimum={0}
                        maximum={100}
                        interval={20}
                        dataSource={[{value: 55, target: 75}]}>
                        <BulletRangeCollectionDirective>
                            <BulletRangeDirective end={35} ></BulletRangeDirective>
                            <BulletRangeDirective end={50} ></BulletRangeDirective>
                            <BulletRangeDirective end={100} ></BulletRangeDirective>
                        </BulletRangeCollectionDirective>
            </BulletChartComponent>);
  }
};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

## Feature Bar Types

You can customize the shape of the feature bar or value bar using the `type` property of the bullet chart. Feature bar contains `Rect` and `Dot` shapes. The default type of feature bar is `Rect`.

{% tab template="bullet-chart/value-bar", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import { BulletChartComponent, Inject} from '@syncfusion/ej2-react-charts';
import { BulletRangeCollectionDirective, BulletRangeDirective} from '@syncfusion/ej2-react-charts';
import * as React from "react";
import * as ReactDOM from "react-dom";

class App extends React.Component<{}, {}>{
  render() {
    return (<BulletChartComponent id='ranges'
                animation={{ enable: false }}
                        valueField='value'
                        targetField='target'
                        title='Sales Rate'
                        type='Dot'
                        minimum={0}
                        maximum={100}
                        interval={20}
                        dataSource={[{value: 55, target: 75}]}>
                        <BulletRangeCollectionDirective>
                            <BulletRangeDirective end={35} ></BulletRangeDirective>
                            <BulletRangeDirective end={50} ></BulletRangeDirective>
                            <BulletRangeDirective end={100} ></BulletRangeDirective>
                        </BulletRangeCollectionDirective>
            </BulletChartComponent>);
  }
};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

## Customization

### Border Customization

Using the `valueBorder` property of the bullet chart, you can customize the border `color` and `width` of the feature bar.

{% tab template="bullet-chart/value-bar", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import { BulletChartComponent, Inject} from '@syncfusion/ej2-react-charts';
import { BulletRangeCollectionDirective, BulletRangeDirective} from '@syncfusion/ej2-react-charts';
import * as React from "react";
import * as ReactDOM from "react-dom";

class App extends React.Component<{}, {}>{
  render() {
    return (<BulletChartComponent id='ranges'
                animation={{ enable: false }}
                        valueField='value'
                        targetField='target'
                        title='Sales Rate'
                        valueBorder={{color: 'red', width: 3}}
                        minimum={0}
                        maximum={100}
                        interval={20}
                        dataSource={[{value: 55, target: 75}]}>
                        <BulletRangeCollectionDirective>
                            <BulletRangeDirective end={35} ></BulletRangeDirective>
                            <BulletRangeDirective end={50} ></BulletRangeDirective>
                            <BulletRangeDirective end={100} ></BulletRangeDirective>
                        </BulletRangeCollectionDirective>
            </BulletChartComponent>);
  }
};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

### Fill color and height Customization

You can customize the fill color and height of the feature bar using the `valueFill` and `valueHeight` properties of the bullet chart.

{% tab template="bullet-chart/value-bar", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import { BulletChartComponent, Inject} from '@syncfusion/ej2-react-charts';
import { BulletRangeCollectionDirective, BulletRangeDirective} from '@syncfusion/ej2-react-charts';
import * as React from "react";
import * as ReactDOM from "react-dom";

class App extends React.Component<{}, {}>{
  render() {
    return (<BulletChartComponent id='ranges'
                animation={{ enable: false }}
                        valueField='value'
                        targetField='target'
                        title='Sales Rate'
                        valueFill='blue'
                        valueHeight={15}
                        minimum={0}
                        maximum={100}
                        interval={20}
                        dataSource={[{value: 55, target: 75}]}>
                        <BulletRangeCollectionDirective>
                            <BulletRangeDirective end={35} ></BulletRangeDirective>
                            <BulletRangeDirective end={50} ></BulletRangeDirective>
                            <BulletRangeDirective end={100} ></BulletRangeDirective>
                        </BulletRangeCollectionDirective>
            </BulletChartComponent>);
  }
};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}