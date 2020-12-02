---
title: " Accumulation Chart Data Label | React "

component: "Accumulation Chart"

description: "Data labels are names of the data points that are displayed on the x-axis of a chart and also used to highlight important data points"
---

# Data Label

Data label can be added to a chart series by enabling the [`visible`](../api/accumulation-chart/accumulationDataLabelSettings/#visible)
option in the dataLabel property.

{% tab template="chart/series/smartlabel", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { AccumulationChartComponent, AccumulationSeriesCollectionDirective, AccumulationSeriesDirective,
 Inject, AccumulationDataLabel,AccumulationDataLabelSettingsModel}
from'@syncfusion/ej2-react-charts';
import { accData } from 'datasource.ts';

class App extends React.Component<{}, {}> {

  public datalabel: AccumulationDataLabelSettingsModel = { visible: true }

  render() {
    return <AccumulationChartComponent id='charts' enableSmartLabels='true'>
      <Inject services={[AccumulationDataLabel]} />
      <AccumulationSeriesCollectionDirective>
        <AccumulationSeriesDirective dataSource={accData} xName='x' yName='y'
          dataLabel={this.datalabel}></AccumulationSeriesDirective>
      </AccumulationSeriesCollectionDirective>
    </AccumulationChartComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

>Note: To use the data label feature, inject the `DataLabel` module into the `services`.

## Positioning

Accumulation chart provides support for placing the data label either `inside` or `outside` the chart.

{% tab template="chart/series/smartlabel", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { AccumulationChartComponent, AccumulationSeriesCollectionDirective, AccumulationSeriesDirective,
 Inject, AccumulationDataLabel,AccumulationDataLabelSettingsModel}
from'@syncfusion/ej2-react-charts';
import { accData } from 'datasource.ts';

class App extends React.Component<{}, {}> {

  public datalabel: AccumulationDataLabelSettingsModel = { visible: true, position: 'Outside' };

  render() {
    return <AccumulationChartComponent id='charts' enableSmartLabels='true'>
      <Inject services={[AccumulationDataLabel]} />
      <AccumulationSeriesCollectionDirective>
        <AccumulationSeriesDirective dataSource={accData} xName='x' yName='y'
          dataLabel={this.datalabel}></AccumulationSeriesDirective>
      </AccumulationSeriesCollectionDirective>
    </AccumulationChartComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

## DataLabel Rotation

Using `angle` property, you can rotate the data label by its given angle.

{% tab template="chart/series/smartlabel", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { AccumulationChartComponent, AccumulationSeriesCollectionDirective, AccumulationSeriesDirective,
 Inject, AccumulationDataLabel,AccumulationDataLabelSettingsModel}
from'@syncfusion/ej2-react-charts';
import { accData } from 'datasource.ts';

class App extends React.Component<{}, {}> {

  public datalabel: AccumulationDataLabelSettingsModel = { visible: true, angle: 90, enableRotation: true};
  render() {
    return <AccumulationChartComponent id='charts' enableSmartLabels='true'>
      <Inject services={[AccumulationDataLabel]} />
      <AccumulationSeriesCollectionDirective>
        <AccumulationSeriesDirective dataSource={accData} xName='x' yName='y'
          dataLabel={this.datalabel}></AccumulationSeriesDirective>
      </AccumulationSeriesCollectionDirective>
    </AccumulationChartComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

>Note: By default, when the `enableRotation` is true, the datalabel is rotated along the slice.

## Smart Labels

Datalabels will be arranged smartly without overlapping with each other. You can enable or disable this feature using
the [`enableSmartLabels`](../api/accumulation-chart/#enablesmartlabels) property.

{% tab template="chart/series/smartlabel", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { AccumulationChartComponent, AccumulationSeriesCollectionDirective, AccumulationSeriesDirective,
 Inject, AccumulationDataLabel,AccumulationDataLabelSettingsModel}
from'@syncfusion/ej2-react-charts';
import { accData } from 'datasource.ts';

class App extends React.Component<{}, {}> {

  public datalabel: AccumulationDataLabelSettingsModel = { visible: true, name: 'text', position: 'Outside' };

  render() {
    return <AccumulationChartComponent id='charts' enableSmartLabels='true'>
      <Inject services={[AccumulationDataLabel]} />
      <AccumulationSeriesCollectionDirective>
        <AccumulationSeriesDirective dataSource={accData} xName='x' yName='y'
          dataLabel={this.datalabel}></AccumulationSeriesDirective>
      </AccumulationSeriesCollectionDirective>
    </AccumulationChartComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

## Datalabel template

Label content can be formatted by using the template option. Inside the template, you can add the placeholder text
`${point.x}` and `${point.y}` to display corresponding data points x & y value. Using
[`template`](../api/accumulation-chart/accumulationDataLabelSettings/#template)property, you can set data label
template in chart.

{% tab template="chart/series/smartlabel", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { AccumulationChartComponent, AccumulationSeriesCollectionDirective, AccumulationSeriesDirective,
Inject, AccumulationDataLabel,AccumulationDataLabelSettingsModel}
from'@syncfusion/ej2-react-charts';
import { accData } from 'datasource.ts';

class App extends React.Component<{}, {}> {

  public template:any =this.chartTemplate;
  public datalabel: AccumulationDataLabelSettingsModel = { visible: true, name: 'text', position: 'Outside', template: this.template };
  public chartTemplate(args:any){
      return (<div id="templateWrap">
          <div>{args.point.x}</div>
          <div>{args.point.y}</div>
        </div>);
  }

  render() {
    return <AccumulationChartComponent id='charts'>
      <Inject services={[AccumulationDataLabel]} />
      <AccumulationSeriesCollectionDirective>
        <AccumulationSeriesDirective dataSource={accData} xName='x' yName='y' dataLabel={this.datalabel}>
        </AccumulationSeriesDirective>
      </AccumulationSeriesCollectionDirective>
    </AccumulationChartComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

## Connector Line

Connector line will be visible when the data label is placed `outside` the chart.
The connector line can be customized using the `type`, `color`, `width`, `length` and `dashArray` properties

{% tab template="chart/series/smartlabel", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { AccumulationChartComponent, AccumulationSeriesCollectionDirective, AccumulationSeriesDirective,
Inject, AccumulationDataLabel,AccumulationDataLabelSettingsModel}
from'@syncfusion/ej2-react-charts';
import { accData } from 'datasource.ts';

class App extends React.Component<{}, {}> {

  public datalabel: AccumulationDataLabelSettingsModel = {
    visible: true, name: 'text', position: 'Outside',
    connectorStyle: {
      //Length of the connector line in pixels
      length: '50px',
      //Width of the connector line in pixels
      width: 2,
      //dashArray of the connector line
      dashArray: '5,3',
      //Color of the connector line
      color: '#f4429e',
      //Specifies the type of the connector line either Line or Curve
      type: 'Curve'
    }
  };

  render() {
    return <AccumulationChartComponent id='charts' enableSmartLabels='true'>
      <Inject services={[AccumulationDataLabel]} />
      <AccumulationSeriesCollectionDirective>
        <AccumulationSeriesDirective dataSource={accData} xName='x' yName='y' dataLabel={this.datalabel}>
        </AccumulationSeriesDirective>
      </AccumulationSeriesCollectionDirective>
    </AccumulationChartComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

## Text Mapping

The fill color and the text in the data source can be mapped to the chart using `pointColorMapping` and `name`
properties, respectively.

{% tab template="chart/series/startangle", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { AccumulationChartComponent, AccumulationSeriesCollectionDirective, AccumulationSeriesDirective,
 Inject, AccumulationDataLabel,AccumulationDataLabelSettingsModel}
from'@syncfusion/ej2-react-charts';
import { dataMapping } from 'datasource.ts';

class App extends React.Component<{}, {}> {

  public datalabel: AccumulationDataLabelSettingsModel = { visible: true, name: 'text', position: 'Outside' };

  render() {
    return <AccumulationChartComponent id='charts'>
      <Inject services={[AccumulationDataLabel]} />
      <AccumulationSeriesCollectionDirective>
        <AccumulationSeriesDirective dataSource={dataMapping} xName='x' yName='y' dataLabel={this.datalabel}>
        </AccumulationSeriesDirective>
      </AccumulationSeriesCollectionDirective>
    </AccumulationChartComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

## Customization

Individual text can be customized using the `textRender` event.

{% tab template="chart/series/smartlabel", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { AccumulationChartComponent, AccumulationSeriesCollectionDirective,AccumulationDataLabelSettingsModel,
 IAccTextRenderEventArgs, AccumulationSeriesDirective, Inject, AccumulationDataLabel}
from'@syncfusion/ej2-react-charts';
import { accData } from 'datasource.ts';

class App extends React.Component<{}, {}> {

  public textRender = (args: IAccTextRenderEventArgs): void => {
    if (args.text === '7') {
      args.color = 'red';
      args.border.width = 1;
    }
  };
  public datalabel: AccumulationDataLabelSettingsModel = { visible: true };

  render() {
    return <AccumulationChartComponent id='charts' enableSmartLabels='true' textRender={this.textRender}>
      <Inject services={[AccumulationDataLabel]} />
      <AccumulationSeriesCollectionDirective>
        <AccumulationSeriesDirective dataSource={accData} xName='x' yName='y' dataLabel={this.datalabel}>
        </AccumulationSeriesDirective>
      </AccumulationSeriesCollectionDirective>
    </AccumulationChartComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}