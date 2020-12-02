---
title: " Bullet Chart Target Bar | React "

component: "Bullet Chart"

description: "The line marker that runs perpendicular to the orientation of the graph is known as the `Comparative Measure`. "
---

# Target Bar

The line marker that runs perpendicular to the orientation of the graph is known as the `Comparative Measure` and is used as a target marker to compare against the Feature Measure value. This is also called as `Target Bar` of the bullet chart. Also, if you want to display the target bar you should map the `targetField` name from the dataSource.

{% tab template="bullet-chart/target-bar", sourceFiles="app/**/*.tsx", compileJsx=true %}

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

## Target Bar Types

You can customize the shape of the target bar or comparative bar using the `targetTypes` property of the bullet chart. Target bar contains `Circle`, `Cross`, and `Rect` shapes. The default type of target bar is `Rect`.

{% tab template="bullet-chart/target-bar", sourceFiles="app/**/*.tsx", compileJsx=true %}

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
                        targetTypes={['Circle']}
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

### Color Customization

Using the `targetColor` property of the bullet chart, you can customize the fill color of the target bar.

{% tab template="bullet-chart/target-bar", sourceFiles="app/**/*.tsx", compileJsx=true %}

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
                        targetColor='red'
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

### Width Customization

You can customize the width of the target bar using the `targetWidth` property of the bullet chart.

{% tab template="bullet-chart/target-bar", sourceFiles="app/**/*.tsx", compileJsx=true %}

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
                        targetWidth={15}
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