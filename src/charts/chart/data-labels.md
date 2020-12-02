---
title: " Chart DataLabel | React "

component: "Chart"

description: "Data labels are names of the data points that are displayed on the x-axis of a chart and also used to highlight important data points"
---

# Data Labels

Data label can be added to a chart series by enabling the [`visible`](../api/chart/dataLabelSettings/#visible)
option in the dataLabel. By default, the labels will arrange smartly without overlapping.

{% tab template="chart/data-marker/datalabel", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { AxisModel, ChartComponent, SeriesCollectionDirective, SeriesDirective, Inject,
         Legend, DateTime, Tooltip, DataLabel, LineSeries}
from'@syncfusion/ej2-react-charts';
import { data } from 'datasource.ts';

class App extends React.Component<{}, {}> {

  public primaryxAxis: AxisModel = { valueType: 'DateTime' };
  public marker = {
    visible: true,
    height: 10, width: 10,
    shape: 'Pentagon',
    dataLabel: { visible: true }
  };

  render() {
    return <ChartComponent id='charts'
      primaryXAxis={this.primaryxAxis}>
      <Inject services={[LineSeries, Legend, Tooltip, DataLabel, DateTime]} />
      <SeriesCollectionDirective>
        <SeriesDirective dataSource={data} xName='x' yName='y' width={2} name='Warmest'
          type='Line' marker={this.marker}>
        </SeriesDirective>
      </SeriesCollectionDirective>
    </ChartComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

>Note: To use data label feature, we need to inject `DataLabel` module into the `services`.

## Position

Using [`position`](../api/chart/dataLabelSettings/#position) property, you can place the label either
on `Top`, `Middle`,`Bottom` or `Outer` (outer is applicable for column and bar type series).

{% tab template="chart/data-marker/datalabel1", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { AxisModel, ChartComponent, SeriesCollectionDirective, SeriesDirective, Inject,
         Legend, Category, Tooltip, DataLabel, LineSeries}
from'@syncfusion/ej2-react-charts';
import { data } from 'datasource.ts';

class App extends React.Component<{}, {}> {

  public primaryxAxis: AxisModel = { title: 'Months', valueType: 'Category' };
  public marker = { dataLabel: { visible: true, position: 'Middle' } };

  render() {
    return <ChartComponent id='charts'
      primaryXAxis={this.primaryxAxis}>
      <Inject services={[LineSeries, Legend, Tooltip, DataLabel, Category]} />
      <SeriesCollectionDirective>
        <SeriesDirective dataSource={data} xName='x' yName='y' width={2} name='Warmest'
          type='Line' marker={this.marker}>
        </SeriesDirective>
      </SeriesCollectionDirective>
    </ChartComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

>Note: The position `Outer` is applicable for column and bar type series.

## Datalabel template

Label content can be formatted by using the template option. Inside the template, you can add the placeholder
text `${point.x}` and `${point.x}` to display corresponding data points x & y value. Using
[`template`](../api/chart/dataLabelSettings/#template) property, you can set data label template in chart.

{% tab template="chart/data-marker/datalabel-template", sourceFiles="app/**/*.tsx", compileJsx=true %}
{% raw %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { AxisModel, ChartComponent, SeriesCollectionDirective, SeriesDirective, Inject,
         Legend, Category, Tooltip, DataLabel, LineSeries}
from'@syncfusion/ej2-react-charts';
import { data } from 'datasource.ts';

class App extends React.Component<{}, {}> {

  public primaryxAxis: AxisModel = { title: 'Months', valueType: 'Category' };
  public template:any =this.chartTemplate;
  public marker = { dataLabel: { visible: true, position: 'Middle', template: this.template } };
  public chartTemplate(args:any){
        return (<div id="templateWrap" style={{ border:'1px solid black', backgroundColor:'red', padding:'3px 3px 3px 3px'}}>
          <div>{args.point.x}</div>
          <div>{args.point.y}</div>
        </div>);
  }
  render() {
    return <ChartComponent id='charts'
      primaryXAxis={this.primaryxAxis}>
      <Inject services={[LineSeries, Legend, Tooltip, DataLabel, Category]} />
      <SeriesCollectionDirective>
        <SeriesDirective dataSource={data} xName='x' yName='y' width={2} name='Warmest'
          type='Line' marker={this.marker}>
        </SeriesDirective>
      </SeriesCollectionDirective>
    </ChartComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endraw %}
{% endtab %}

## Text Mapping

Text from the data source can be mapped using `name` property.

{% tab template="chart/data-marker/datalabel", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { AxisModel, ChartComponent, SeriesCollectionDirective, SeriesDirective, Inject,
         Legend, Category, Tooltip, DataLabel, ColumnSeries}
from'@syncfusion/ej2-react-charts';
import { mapData } from 'datasource.ts';

class App extends React.Component<{}, {}> {

  public primaryxAxis: AxisModel = { valueType: 'Category' };
  public marker = { dataLabel: { visible: true, name: 'text' } };

  render() {
    return <ChartComponent id='charts'
      primaryXAxis={this.primaryxAxis}>
      <Inject services={[ColumnSeries, Legend, Tooltip, DataLabel, Category]} />
      <SeriesCollectionDirective>
        <SeriesDirective dataSource={mapData} xName='x' yName='y'
          type='Column' marker={this.marker}>
        </SeriesDirective>
      </SeriesCollectionDirective>
    </ChartComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

## Margin

`margin` for data label can be applied to using `left`, `right`, `bottom` and `top` properties.

{% tab template="chart/data-marker/datalabel", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { AxisModel, ChartComponent, SeriesCollectionDirective, SeriesDirective, Inject,
         Legend, Category, Tooltip, DataLabel, ColumnSeries}
from'@syncfusion/ej2-react-charts';
import { columnData } from 'datasource.ts';

class App extends React.Component<{}, {}> {

  public primaryxAxis: AxisModel = { valueType: 'Category' };
  public marker = {
    dataLabel: {
      visible: true, border: { width: 1, color: 'red' },
      margin: {
        left: 5,
        right: 5,
        top: 5,
        bottom: 5
      }
    }
  };

  render() {
    return <ChartComponent id='charts'
      primaryXAxis={this.primaryxAxis}>
      <Inject services={[ColumnSeries, Legend, Tooltip, DataLabel, Category]} />
      <SeriesCollectionDirective>
        <SeriesDirective dataSource={columnData} xName='country' yName='gold'
          type='Column' marker={this.marker}>
        </SeriesDirective>
      </SeriesCollectionDirective>
    </ChartComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

## DataLabel Rotation

Using `angle` property, you can rotate the data label by its given angle.

{% tab template="chart/data-marker/marker", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { AxisModel, ChartComponent, SeriesCollectionDirective, SeriesDirective, Inject,
         Legend, Category, Tooltip, DataLabel, ColumnSeries}
from'@syncfusion/ej2-react-charts';
import { columnData } from 'datasource.ts';

class App extends React.Component<{}, {}> {

  public primaryxAxis: AxisModel = { valueType: 'Category' };
  public marker = {
    //Data label angle as 45
    dataLabel: {
      visible: true, border: { width: 1, color: 'red' },
      margin: {
        left: 5,
        right: 5,
        top: 5,
        bottom: 5
      }, angle: 45, enableRotation: true
    }
  };

  render() {
    return <ChartComponent id='charts'
      primaryXAxis={this.primaryxAxis}>
      <Inject services={[ColumnSeries, Legend, Tooltip, DataLabel, Category]} />
      <SeriesCollectionDirective>
        <SeriesDirective dataSource={columnData} xName='country' yName='gold'
          type='Column' marker={this.marker}>
        </SeriesDirective>
      </SeriesCollectionDirective>
    </ChartComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

## Customization

`stroke` and `border` of data label can be customized using `fill` and `border` properties.
Rounded corners can be customized using `rx` and `ry` properties.

{% tab template="chart/data-marker/datalabel", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import { AxisModel, ChartComponent, SeriesCollectionDirective, SeriesDirective, Inject,
         Legend, Category, Tooltip, DataLabel, ColumnSeries}
from'@syncfusion/ej2-react-charts';
import { columnData } from 'datasource.ts';

class App extends React.Component<{}, {}> {

  public primaryxAxis: AxisModel = { valueType: 'Category' };
  public marker = {
    dataLabel: {
      visible: true, bborder: { width: 2, color: 'red' },
      rx: 10, ry: 10
    }
  };

  render() {
    return <ChartComponent id='charts'
      primaryXAxis={this.primaryxAxis}>
      <Inject services={[ColumnSeries, Legend, Tooltip, DataLabel, Category]} />
      <SeriesCollectionDirective>
        <SeriesDirective dataSource={columnData} xName='country' yName='gold'
          type='Column' marker={this.marker}>
        </SeriesDirective>
      </SeriesCollectionDirective>
    </ChartComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

>Note: `rx` and `ry` properties requires `border` values not to be null.

## Customizing Specific Point

You can also customize the specific marker and label using
[`pointRender`](../api/chart/chartModel/#pointrender) and
[`textRender`](../api/chart/chartModel/#textrender/) event. `pointRender` event
allows you to change the shape, color and border for a point, whereas the `textRender` event allows you
to change the text for the point.

{% tab template="chart/data-marker/datalabel1", sourceFiles="app/**/*.tsx", compileJsx=true %}

```tsx
import * as React from "react";
import * as ReactDOM from "react-dom";
import {  AxisModel, ChartComponent, SeriesCollectionDirective, SeriesDirective, Inject,
         Legend, Category, Tooltip, DataLabel, LineSeries}
from'@syncfusion/ej2-react-charts';
import { data } from 'datasource.ts';

class App extends React.Component<{}, {}> {

  public pointRender: EmitType<IPointRenderEventArgs> = (args: IPointRenderEventArgs): void => {
    if (args.point.index === 6) {
      args.fill = 'red'
    }
  };
  public primaryxAxis: AxisModel = { valueType: 'Category' };
  public marker = { dataLabel: { visible: true, position: 'Middle' } };

  render() {
    return <ChartComponent id='charts'
      primaryXAxis={this.primaryxAxis}
      pointRender={this.pointRender}
      title='Alaska Weather Statistics - 2016'>
      <Inject services={[LineSeries, Legend, Tooltip, DataLabel, Category]} />
      <SeriesCollectionDirective>
        <SeriesDirective dataSource={data} xName='x' yName='y'
          type='Line' marker={this.marker}>
        </SeriesDirective>
      </SeriesCollectionDirective>
    </ChartComponent>
  }

};
ReactDOM.render(<App />, document.getElementById("charts"));
```

{% endtab %}

## See Also

* [Show total stacking values in data label](./how-to/#show-the-total-value-for-stacking-series-in-data-label)
* [Prevent the data label when the data value is 0](./how-to/#prevent-the-data-label-when-the-data-value-is-0)