---
title: "Accumulation Chart Legend | TypeScript "

component: "Accumulation Chart"

description: "Accumulation chart legend is used to give additional information about the chart series."
---

# Legend

As like a chart, the legend is also available for accumulation charts, which gives information about the points.
By default, the legend will be placed on the right, if the width of the chart is high or will be placed on the bottom,
if the height of the chart is high. Other customization features regarding the legend element are same as the
[`chart legend`](http://ej2.syncfusion.com/documentation/chart/legend.html#position-and-alignment).
Here, the legend for a point can be collapsed by giving the empty string to the x value of the point.

{% tab template="chart/series/legend", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { AccumulationChartComponent, AccumulationSeriesCollectionDirective, AccumulationSeriesDirective,
 Inject, AccumulationLegend,LegendSettingsModel}
from'@syncfusion/ej2-react-charts';
import { accData } from 'datasource.ts';

class App extends React.Component<{}, {}> {

  public legendSettings: LegendSettingsModel = { visible: true };

  render() {
    return <AccumulationChartComponent id='charts' legendSettings={this.legendSettings}>
      <Inject services={[AccumulationLegend]} />
      <AccumulationSeriesCollectionDirective>
        <AccumulationSeriesDirective dataSource={accData} xName='x' yName='y'>
        </AccumulationSeriesDirective>
      </AccumulationSeriesCollectionDirective>
    </AccumulationChartComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

>Note: To use the legends feature, inject the `AccumulationLegend` using the module
into the `services`.

## Position and Alignment

By using the position property, you can position the legend at the `left`, `right`, `top` or `bottom` of the chart.
You can also align the legend to `center`, `far` or `near` of the chart using the alignment property.

{% tab template="chart/series/legend", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { AccumulationChartComponent, AccumulationSeriesCollectionDirective, AccumulationSeriesDirective,
 Inject, AccumulationLegend,LegendSettingsModel}
from'@syncfusion/ej2-react-charts';
import { accData } from 'datasource.ts';

class App extends React.Component<{}, {}> {

  public legendSettings: LegendSettingsModel = { position: 'Right', visible: true, height: '40', width: '160' };

  render() {
    return <AccumulationChartComponent id='charts' legendSettings={this.legendSettings}>
      <Inject services={[AccumulationLegend]} />
      <AccumulationSeriesCollectionDirective>
        <AccumulationSeriesDirective dataSource={accData} xName='x' yName='y'>
        </AccumulationSeriesDirective>
      </AccumulationSeriesCollectionDirective>
    </AccumulationChartComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

## Legend Shape

To change the legend icon shape, use the `legendShape` property in the `series`. By default, legend icon shape
is `seriesType`.

{% tab template="chart/series/legend", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { AccumulationChartComponent, AccumulationSeriesCollectionDirective, AccumulationSeriesDirective, Inject,
AccumulationLegend,LegendSettingsModel}
from'@syncfusion/ej2-react-charts';
import { accData } from 'datasource.ts';

class App extends React.Component<{}, {}> {

  public legendSettings: LegendSettingsModel = { position: 'Right', visible: true, height: '40', width: '160' };

  render() {
    return <AccumulationChartComponent id='charts' legendSettings={this.legendSettings}>
      <Inject services={[AccumulationLegend]} />
      <AccumulationSeriesCollectionDirective>
        <AccumulationSeriesDirective dataSource={accData} xName='x' yName='y' legendShape='Rectangle'></AccumulationSeriesDirective>
      </AccumulationSeriesCollectionDirective>
    </AccumulationChartComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

## Legend Size

The legend size can be changed by using the `width` and `height` properties of the `legendSettings`.

{% tab template="chart/series/legend", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { AccumulationChartComponent, AccumulationSeriesCollectionDirective, AccumulationSeriesDirective, Inject,
 AccumulationLegend,LegendSettingsModel}
from'@syncfusion/ej2-react-charts';
import { accData } from 'datasource.ts';

class App extends React.Component<{}, {}> {

  public legendSettings: LegendSettingsModel = { width: '150', height: '100', border: { width: 1, color: 'pink' } };

  render() {
    return <AccumulationChartComponent id='charts' legendSettings={this.legendSettings}>
      <Inject services={[AccumulationLegend]} />
      <AccumulationSeriesCollectionDirective>
        <AccumulationSeriesDirective dataSource={accData} xName='x' yName='y' legendShape='Circle'></AccumulationSeriesDirective>
      </AccumulationSeriesCollectionDirective>
    </AccumulationChartComponent>
  }

};

ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

## Legend Item Size

You can customize the size of the legend items by using the `shapeHeight` and `shapeWidth` properties.

{% tab template="chart/series/legend", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { AccumulationChartComponent, AccumulationSeriesCollectionDirective, AccumulationSeriesDirective, Inject, AccumulationLegend,LegendSettingsModel}
from'@syncfusion/ej2-react-charts';
import { accData } from 'datasource.ts';

class App extends React.Component<{}, {}> {

  public legendSettings: LegendSettingsModel = { shapeHeight: 15, shapeWidth: 15 };

  render() {
    return <AccumulationChartComponent id='charts' legendSettings={this.legendSettings}>
      <Inject services={[AccumulationLegend]} />
      <AccumulationSeriesCollectionDirective>
        <AccumulationSeriesDirective dataSource={accData} xName='x' yName='y' legendShape='Circle'></AccumulationSeriesDirective>
      </AccumulationSeriesCollectionDirective>
    </AccumulationChartComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

## Paging for Legend

Paging will be enabled by default, when the legend items exceeds the legend bounds. You can view the each legend
item by navigating between the pages using the navigation buttons.

{% tab template="chart/series/legend", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { AccumulationChartComponent, AccumulationSeriesCollectionDirective, AccumulationSeriesDirective, Inject, AccumulationLegend,LegendSettingsModel}
from'@syncfusion/ej2-react-charts';
import { accData } from 'datasource.ts';

class App extends React.Component<{}, {}> {

  public legendSettings: LegendSettingsModel = { height: '150', width: '80' };

  render() {
    return <AccumulationChartComponent id='charts' legendSettings={this.legendSettings}>
      <Inject services={[AccumulationLegend]} />
      <AccumulationSeriesCollectionDirective>
        <AccumulationSeriesDirective dataSource={accData} xName='x' yName='y' legendShape='Circle'></AccumulationSeriesDirective>
      </AccumulationSeriesCollectionDirective>
    </AccumulationChartComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

## Enable Animation

You can customize the animation while clicking legend by setting enableAnimation as true or false using
`enableAnimation` property in Accumulation Chart.

{% tab template="chart/series/legend", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { AccumulationChartComponent, AccumulationSeriesCollectionDirective, AccumulationSeriesDirective, Inject, AccumulationLegend,TooltipSettingsModel,AccumulationTooltip,LegendSettingsModel, AccumulationDataLabelSettingsModel,AccumulationDataLabel}
from'@syncfusion/ej2-react-charts';
import { data1 } from 'datasource.ts';

class App extends React.Component<{}, {}> {

  public legendSettings: LegendSettingsModel = { height: '150', width: '80' };
  public datalabel: AccumulationDataLabelSettingsModel = { visible: true,
                    name: 'text',
                    position: 'Inside',
                    font: {
                        fontWeight: '600',
                        color: '#ffffff'
                    }
 };
 public tooltip: TooltipSettingsModel = { enable: false };

  render() {
    return <AccumulationChartComponent id='charts' legendSettings={this.legendSettings} tooltip={this.tooltip} title='Project Cost Breakdown' >
      <Inject services={[AccumulationLegend,AccumulationDataLabel,AccumulationTooltip]} />
      <AccumulationSeriesCollectionDirective>
        <AccumulationSeriesDirective dataSource={data1} xName='x' yName='y' legendShape='Circle' dataLabel={this.datalabel}
         startAngle='0' endAngle='360' explode={true} explodeOffset='10%' explodeIndex={3} name='Project' radius='70%' innerRadius='40%'>
        </AccumulationSeriesDirective>
      </AccumulationSeriesCollectionDirective>
    </AccumulationChartComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

## Legend Title

You can set title for legend using `title` property in `legendSettings`. You can also customize the `fontStyle`, `size`, `fontWeight`, `color`, `textAlignment`, `fontFamily`, `opacity` and `textOverflow` of legend title. `titlePosition` is used to set the legend position in `Top`, `Left` and `Right` position. `maximumTitleWidth` is used to set the width of the legend title. By default, it will be `100px`.

{% tab template="chart/series/legend", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { AccumulationChartComponent, AccumulationSeriesCollectionDirective, AccumulationSeriesDirective, Inject, AccumulationLegend,LegendSettingsModel}
from'@syncfusion/ej2-react-charts';
import { data } from 'datasource.ts';

class App extends React.Component<{}, {}> {

  public legendSettings: LegendSettingsModel = { title: 'Months', position: 'Bottom' };

  render() {
    return <AccumulationChartComponent id='charts' legendSettings={this.legendSettings}>
      <Inject services={[AccumulationLegend]} />
      <AccumulationSeriesCollectionDirective>
        <AccumulationSeriesDirective dataSource={data} xName='x' yName='y'></AccumulationSeriesDirective>
      </AccumulationSeriesCollectionDirective>
    </AccumulationChartComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

## Arrow Page Navigation

By default, the page number will be enabled while legend paging. Now, you can disable that page number and also you can get left and right arrows for page navigation. You have to set `false` value to `enablePages` to get this support.

{% tab template="chart/series/legend", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { AccumulationChartComponent, AccumulationSeriesCollectionDirective, AccumulationSeriesDirective, Inject, AccumulationLegend,LegendSettingsModel}
from'@syncfusion/ej2-react-charts';
import { data } from 'datasource.ts';

class App extends React.Component<{}, {}> {

  public legendSettings: LegendSettingsModel = { width: '260px', height: '50px', enablePages: false, position: 'Bottom' };

  render() {
    return <AccumulationChartComponent id='charts' legendSettings={this.legendSettings}>
      <Inject services={[AccumulationLegend]} />
      <AccumulationSeriesCollectionDirective>
        <AccumulationSeriesDirective dataSource={data} xName='x' yName='y'></AccumulationSeriesDirective>
      </AccumulationSeriesCollectionDirective>
    </AccumulationChartComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}