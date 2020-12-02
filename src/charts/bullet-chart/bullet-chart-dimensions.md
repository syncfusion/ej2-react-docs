---
title: " Bullet Chart Appearance | React "

component: "Bullet Chart"

description: "We can set bullet-chart size manually by using width and height properties. We can set percentage or pixel size values to the bullet-chart."
---

# Bullet Chart Dimensions

## Size for Container

The bullet chart can be rendered to its container’s size. You can set the size using inline or CSS as shown below.

```html
 <div id="charts" style="width:650px; height:350px"></div>
```

{% tab template="bullet-chart/bullet-chart-dimensions/container", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import { BulletChartComponent, Inject} from '@syncfusion/ej2-react-charts';
import { BulletRangeCollectionDirective, BulletRangeDirective} from '@syncfusion/ej2-react-charts';
import * as React from "react";
import * as ReactDOM from "react-dom";

class App extends React.Component<{}, {}>{
  render() {
    return (<BulletChartComponent id='ranges'
                        animation={{ enable: false }}
                        width="80%"
                        height="90%"
                        valueField='value'
                        targetField='target'
                        title='Revenue'
                        minimum={0}
                        maximum={30}
                        interval={5}
                        dataSource={[{value: 23, target: 22}]}>
                        <BulletRangeCollectionDirective>
                            <BulletRangeDirective end={20} color='red' ></BulletRangeDirective>
                            <BulletRangeDirective end={25} color='blue'></BulletRangeDirective>
                            <BulletRangeDirective end={30} color='green'></BulletRangeDirective>
                        </BulletRangeCollectionDirective>

            </BulletChartComponent>);
  }
};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

## Size for Bullet Chart

You can also set the size for bullet chart directly using the [`width`](../api/bullet-chart/bulletChartModel/#width) and [`height`](../api/bullet-chart/bulletChartModel/#height) properties.

{% tab template="bullet-chart/bullet-chart-dimensions/container", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import { BulletChartComponent, Inject} from '@syncfusion/ej2-react-charts';
import { BulletRangeCollectionDirective, BulletRangeDirective} from '@syncfusion/ej2-react-charts';
import * as React from "react";
import * as ReactDOM from "react-dom";

class App extends React.Component<{}, {}>{
  render() {
    return (<BulletChartComponent id='ranges'
                        animation={{ enable: false }}
                        width="80%"
                        height="90%"
                        valueField='value'
                        targetField='target'
                        title='Revenue'
                        minimum={0}
                        maximum={30}
                        interval={5}
                        dataSource={[{value: 23, target: 22}]}>
                        <BulletRangeCollectionDirective>
                            <BulletRangeDirective end={20} color='red' ></BulletRangeDirective>
                            <BulletRangeDirective end={25} color='blue'></BulletRangeDirective>
                            <BulletRangeDirective end={30} color='green'></BulletRangeDirective>
                        </BulletRangeCollectionDirective>
            </BulletChartComponent>);
  }
};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

### In Pixel

You can set the size of a chart in pixels as shown below.

{% tab template="bullet-chart/bullet-chart-dimensions/container", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import { BulletChartComponent, Inject} from '@syncfusion/ej2-react-charts';
import { BulletRangeCollectionDirective, BulletRangeDirective} from '@syncfusion/ej2-react-charts';
import * as React from "react";
import * as ReactDOM from "react-dom";

class App extends React.Component<{}, {}>{
  render() {
    return (<BulletChartComponent id='ranges'
                        animation={{ enable: false }}
                        width="600px"
                        height="100px"
                        valueField='value'
                        targetField='target'
                        title='Revenue'
                        minimum={0}
                        maximum={30}
                        interval={5}
                        dataSource={[{value: 23, target: 22}]}>
                        <BulletRangeCollectionDirective>
                            <BulletRangeDirective end={20} color='red' ></BulletRangeDirective>
                            <BulletRangeDirective end={25} color='blue'></BulletRangeDirective>
                            <BulletRangeDirective end={30} color='green'></BulletRangeDirective>
                        </BulletRangeCollectionDirective>

            </BulletChartComponent>);
  }
};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

### In Percentage

By setting a value in percentage, the bullet chart gets its dimension with respect to its container. For example, when the height is ‘50%’, the bullet chart renders to half of the container’s height.

{% tab template="bullet-chart/bullet-chart-dimensions/container", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import { BulletChartComponent, Inject} from '@syncfusion/ej2-react-charts';
import { BulletRangeCollectionDirective, BulletRangeDirective} from '@syncfusion/ej2-react-charts';
import * as React from "react";
import * as ReactDOM from "react-dom";

class App extends React.Component<{}, {}>{
  render() {
    return (<BulletChartComponent id='ranges'
                        animation={{ enable: false }}
                        width="80%"
                        height="90%"
                        valueField='value'
                        targetField='target'
                        title='Revenue'
                        minimum={0}
                        maximum={30}
                        interval={5}
                        dataSource={[{value: 23, target: 22}]}>
                        <BulletRangeCollectionDirective>
                            <BulletRangeDirective end={20} color='red' ></BulletRangeDirective>
                            <BulletRangeDirective end={25} color='blue'></BulletRangeDirective>
                            <BulletRangeDirective end={30} color='green'></BulletRangeDirective>
                        </BulletRangeCollectionDirective>

            </BulletChartComponent>);
  }
};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

>Note: When you do not specify the size, it takes `126px` as its height and window size as its width.