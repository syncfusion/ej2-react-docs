---
title: " Bullet Chart Customization | React "

component: "Bullet Chart"

description: "Bullet Chart have different customizable features like different orientation, flow directions and animation features"
---

# Orientation

Bullet Chart can be rendered in different mode as `Horizontal` or `vertical` by using `orientation` property of the bullet-chart. By default bullet-chart rendered in horizontal mode.

{% tab template="bullet-chart/customization", sourceFiles="app/**/*.tsx", compileJsx=true %}

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
                        title='Sales Rate in dollars'
                        width='20%'
                        orientation='vertical'
                        minimum={0}
                        maximum={100}
                        interval={20}
                        dataSource={[{value: 55, target: 45}]}>
                        <BulletRangeCollectionDirective>
                            <BulletRangeDirective end={35}></BulletRangeDirective>
                            <BulletRangeDirective end={50}></BulletRangeDirective>
                            <BulletRangeDirective end={100}></BulletRangeDirective>
                        </BulletRangeCollectionDirective>
            </BulletChartComponent>);
  }
};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

## Flow Direction

Using `enableRtl` boolean property of the bullet-chart, you can render bullet-chart in right to left or left to right direction.

{% tab template="bullet-chart/customization", sourceFiles="app/**/*.tsx", compileJsx=true %}

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
                        enableRtl={true}
                        minimum={0}
                        maximum={2000}
                        interval={200}
                        dataSource={[{value: 1500, target: 1000}]}>
                        <BulletRangeCollectionDirective>
                            <BulletRangeDirective end={500} color='red' ></BulletRangeDirective>
                            <BulletRangeDirective end={1500} color='blue'></BulletRangeDirective>
                            <BulletRangeDirective end={2000} color='green'></BulletRangeDirective>
                        </BulletRangeCollectionDirective>
            </BulletChartComponent>);
  }
};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

## Animation

By setting `animation` property value as `true`, you can enable the linear animation of the feature and target bars.

{% tab template="bullet-chart/customization", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import { BulletChartComponent, Inject} from '@syncfusion/ej2-react-charts';
import { BulletRangeCollectionDirective, BulletRangeDirective} from '@syncfusion/ej2-react-charts';
import * as React from "react";
import * as ReactDOM from "react-dom";

class App extends React.Component<{}, {}>{
  render() {
    return (<BulletChartComponent id='ranges'
                animation={{ enable: true }}
                        valueField='value'
                        targetField='target'
                        minimum={0}
                        maximum={2000}
                        interval={200}
                        dataSource={[{value: 1500, target: 1000}]}>
                        <BulletRangeCollectionDirective>
                            <BulletRangeDirective end={500} color='red' ></BulletRangeDirective>
                            <BulletRangeDirective end={1500} color='blue'></BulletRangeDirective>
                            <BulletRangeDirective end={2000} color='green'></BulletRangeDirective>
                        </BulletRangeCollectionDirective>
            </BulletChartComponent>);
  }
};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

## Theme

Bullet chart also support different types of themes. Using `theme` property of the bullet-chart, you can customize the theme styles.

{% tab template="bullet-chart/customization", sourceFiles="app/**/*.tsx", compileJsx=true %}

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
                        title='Profit in %'
                        theme='HighContrast'
                        minimum={0}
                        maximum={100}
                        interval={10}
                        dataSource={[{value: 50, target: 45}]}>
                        <BulletRangeCollectionDirective>
                            <BulletRangeDirective end={15} color='red' ></BulletRangeDirective>
                            <BulletRangeDirective end={50} color='blue'></BulletRangeDirective>
                            <BulletRangeDirective end={100} color='green'></BulletRangeDirective>
                        </BulletRangeCollectionDirective>
            </BulletChartComponent>);
  }
};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}