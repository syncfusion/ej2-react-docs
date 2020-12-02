---
title: " Bullet Chart Title and SubTitle | React "

component: "Bullet Chart"

description: "The title and sub-title is very useful to understand the bullet chart in efficient way. It describes what kind of data which represtend by the bullet-chart. "
---

# Title

A title can be given to a bullet chart using the `title` property to show information about the data plotted.

{% tab template="bullet-chart/title", sourceFiles="app/**/*.tsx", compileJsx=true %}

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
                            <BulletRangeDirective end={35} color='red' ></BulletRangeDirective>
                            <BulletRangeDirective end={50} color='blue'></BulletRangeDirective>
                            <BulletRangeDirective end={100} color='green'></BulletRangeDirective>
                        </BulletRangeCollectionDirective>
            </BulletChartComponent>);
  }
};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

## SubTitle

A subtitle can also be given to a bullet chart using the `subtitle` property to show additional information about the data plotted.

{% tab template="bullet-chart/title", sourceFiles="app/**/*.tsx", compileJsx=true %}

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
                        subtitle='(in dollars $)'
                        minimum={0}
                        maximum={100}
                        interval={20}
                        dataSource={[{value: 55, target: 45}]}>
                        <BulletRangeCollectionDirective>
                            <BulletRangeDirective end={35} color='red' ></BulletRangeDirective>
                            <BulletRangeDirective end={50} color='blue'></BulletRangeDirective>
                            <BulletRangeDirective end={100} color='green'></BulletRangeDirective>
                        </BulletRangeCollectionDirective>
            </BulletChartComponent>);
  }
};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

## Title and SubTitle Position

You can place the title and subtitle in different positions. By using the `titlePosition` property of the bullet chart, you can place the title and subtitles in different positions like `left`, `right`, `top`, and `bottom`.

### Position as Left

By setting the `titlePosition` to `Left`, you can display the title and subtitle at the left side of the chart.

{% tab template="bullet-chart/title", sourceFiles="app/**/*.tsx", compileJsx=true %}

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
                        subtitle='(in dollars $)'
                        titlePosition='Left'
                        labelFormat='${value}'
                        minimum={0}
                        maximum={100}
                        interval={20}
                        dataSource={[{value: 55, target: 45}]}>
                        <BulletRangeCollectionDirective>
                            <BulletRangeDirective end={35} color='red' ></BulletRangeDirective>
                            <BulletRangeDirective end={50} color='blue'></BulletRangeDirective>
                            <BulletRangeDirective end={100} color='green'></BulletRangeDirective>
                        </BulletRangeCollectionDirective>
            </BulletChartComponent>);
  }
};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

### Position as Right

By setting the `titlePosition` to `Right`, you can display the title and subtitle at the right side of the chart.

{% tab template="bullet-chart/title", sourceFiles="app/**/*.tsx", compileJsx=true %}

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
                        subtitle='(in dollars $)'
                        titlePosition='Right'
                        labelFormat='${value}'
                        minimum={0}
                        maximum={100}
                        interval={20}
                        dataSource={[{value: 55, target: 45}]}>
                        <BulletRangeCollectionDirective>
                            <BulletRangeDirective end={35} color='red' ></BulletRangeDirective>
                            <BulletRangeDirective end={50} color='blue'></BulletRangeDirective>
                            <BulletRangeDirective end={100} color='green'></BulletRangeDirective>
                        </BulletRangeCollectionDirective>
            </BulletChartComponent>);
  }
};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

### Position as Top

By setting the `titlePosition` to `Top`, you can display the title and subtitle at the top of the chart. The default title and subtitle positions of the bullet chart is `Top`.

{% tab template="bullet-chart/title", sourceFiles="app/**/*.tsx", compileJsx=true %}

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
                        subtitle='(in dollars $)'
                        titlePosition='Top'
                        labelFormat='${value}'
                        minimum={0}
                        maximum={100}
                        interval={20}
                        dataSource={[{value: 55, target: 45}]}>
                        <BulletRangeCollectionDirective>
                            <BulletRangeDirective end={35} color='red' ></BulletRangeDirective>
                            <BulletRangeDirective end={50} color='blue'></BulletRangeDirective>
                            <BulletRangeDirective end={100} color='green'></BulletRangeDirective>
                        </BulletRangeCollectionDirective>
            </BulletChartComponent>);
  }
};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

### Position as Bottom

By setting the `titlePosition` to `Bottom`, you can display the title and subtitle at the bottom of the chart.

{% tab template="bullet-chart/title", sourceFiles="app/**/*.tsx", compileJsx=true %}

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
                        subtitle='(in dollars $)'
                        titlePosition='Bottom'
                        labelFormat='${value}'
                        minimum={0}
                        maximum={100}
                        interval={20}
                        dataSource={[{value: 55, target: 45}]}>
                        <BulletRangeCollectionDirective>
                            <BulletRangeDirective end={35} color='red' ></BulletRangeDirective>
                            <BulletRangeDirective end={50} color='blue'></BulletRangeDirective>
                            <BulletRangeDirective end={100} color='green'></BulletRangeDirective>
                        </BulletRangeCollectionDirective>
            </BulletChartComponent>);
  }
};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

## Title Customization

You can customize the bullet chart title’s `fontStyle`, `size`, `color`, `fontWeight`, and `fontFamily` using the `titleStyle` property.

{% tab template="bullet-chart/title", sourceFiles="app/**/*.tsx", compileJsx=true %}

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
                        subtitle='(in dollars $)'
                        labelFormat='${value}'
                        minimum={0}
                        maximum={100}
                        interval={20}
                        titleStyle={{size: '22px', color:'red', fontFamily:'cursive', fontWeight:'Bold'}}
                        dataSource={[{value: 55, target: 45}]}>
                        <BulletRangeCollectionDirective>
                            <BulletRangeDirective end={35} color='red' ></BulletRangeDirective>
                            <BulletRangeDirective end={50} color='blue'></BulletRangeDirective>
                            <BulletRangeDirective end={100} color='green'></BulletRangeDirective>
                        </BulletRangeCollectionDirective>
            </BulletChartComponent>);
  }
};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

## SubTitle Customization

You can customize the bullet chart subtitle’s `fontStyle`, `size`, `color`, `fontWeight`, and `fontFamily` using the `subtitleStyle` property.

{% tab template="bullet-chart/title", sourceFiles="app/**/*.tsx", compileJsx=true %}

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
                        subtitle='(in dollars $)'
                        labelFormat='${value}'
                        minimum={0}
                        maximum={100}
                        interval={20}
                        subtitleStyle={{size: '22px', color:'red', fontFamily:'cursive', fontWeight:'Bold'}}
                        dataSource={[{value: 55, target: 45}]}>
                        <BulletRangeCollectionDirective>
                            <BulletRangeDirective end={35} color='red' ></BulletRangeDirective>
                            <BulletRangeDirective end={50} color='blue'></BulletRangeDirective>
                            <BulletRangeDirective end={100} color='green'></BulletRangeDirective>
                        </BulletRangeCollectionDirective>
            </BulletChartComponent>);
  }
};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}