---
title: "Tooltip"
component: "Heatmap"
description: "This section describes on how to define tooltip in heatmap and the customization options available for the tooltip"
---

# Tooltip

Tooltip is used to provide the details of the heatmap cell, and this can be displayed, while hovering the cursor over the cell or performing tap action in touch devices.

## Default tooltip

You can enable the tooltip by setting the [`showTooltip`](../api/heatmap/#showtooltip)  property to true and injecting the `Tooltip` module into the `services`.

{% tab template= "heatmap/tooltip", sourceFiles="app/**/*.tsx", compileJsx=true%}

```typescript

import * as React from "react";
import * as ReactDOM from 'react-dom';
import { HeatMapComponent, Inject, Legend, Tooltip } from '@syncfusion/ej2-react-heatmap';

class App extends React.Component {
    private heatmapData: any [] = [
    [0.72, 0.71, 0.71, 0.67, 0.72, 0.53, 0.53, 0.56, 0.58, 0.56],
    [2.28, 2.29, 2.09, 1.84, 1.64, 1.49, 1.49, 1.39, 1.32, 1.23],
    [2.02, 2.17, 2.30, 2.39, 2.36, 2.52, 2.62, 2.57, 2.57, 2.74],
    [3.21, 3.26, 3.45, 3.47, 3.42, 3.34, 3.14, 2.83, 2.64, 2.61],
    [3.22, 3.13, 3.04, 2.95, 2.69, 2.49, 2.27, 2.18, 2.06, 1.87],
    [3.30, 3.39, 3.40, 3.48, 3.60, 3.67, 3.73, 3.79, 3.79, 4.07],
    [5.80, 5.74, 5.64, 5.44, 5.18, 5.08, 5.07, 5.00, 5.35, 5.47],
    [6.91, 7.40, 8.13, 8.80, 9.04, 9.24, 9.43, 9.35, 9.49, 9.69]
    ];
    render() {
    return ( <HeatMapComponent id='heatmap'
            titleSettings = { {
                text: 'Crude Oil Production of Non-OPEC Countries (in Million barrels per day)',
                textStyle: {
                    size: '15px',
                    fontWeight: '500',
                    fontStyle: 'Normal',
                    fontFamily: 'Segoe UI'
                }
            } }
            xAxis = { {
                 labels: ['Canada', 'China', 'Egypt', 'Mexico', 'Norway', 'Russia', 'UK', 'USA']
            } }
            yAxis = { {
                labels: ['2000', '2001', '2002', '2003', '2004', '2005', '2006', '2007', '2008', '2009', '2010'],
            } }
            cellSettings = { {
                 showLabel: false,
            } }
            showTooltip = { true }
            dataSource={this.heatmapData}>
            <Inject services={[Legend, Tooltip]} />
            </HeatMapComponent> );
    }
}
ReactDOM.render(<App />, document.getElementById('heatmap'));

```

{% endtab %}

## Tooltip template

In heatmap, you can customize the tooltip using the [`tooltipRender`](../api/heatmap/#tooltiprender) client side event.

{% tab template= "heatmap/tooltip", sourceFiles="app/**/*.tsx", compileJsx=true%}

```typescript

import * as React from "react";
import * as ReactDOM from 'react-dom';
import { HeatMapComponent, Inject, Legend, Tooltip } from '@syncfusion/ej2-react-heatmap';

class App extends React.Component {
   heatmapData: any[] = [
    [0.72, 0.71, 0.71, 0.67, 0.72, 0.53, 0.53, 0.56, 0.58, 0.56],
    [2.28, 2.29, 2.09, 1.84, 1.64, 1.49, 1.49, 1.39, 1.32, 1.23],
    [2.02, 2.17, 2.3, 2.39, 2.36, 2.52, 2.62, 2.57, 2.57, 2.74],
    [3.21, 3.26, 3.45, 3.47, 3.42, 3.34, 3.14, 2.83, 2.64, 2.61],
    [3.22, 3.13, 3.04, 2.95, 2.69, 2.49, 2.27, 2.18, 2.06, 1.87],
    [3.3, 3.39, 3.4, 3.48, 3.6, 3.67, 3.73, 3.79, 3.79, 4.07],
    [5.8, 5.74, 5.64, 5.44, 5.18, 5.08, 5.07, 5.0, 5.35, 5.47],
    [6.91, 7.4, 8.13, 8.8, 9.04, 9.24, 9.43, 9.35, 9.49, 9.69]
  ];
  render() {
    return (
      <HeatMapComponent
        id="heatmap"
        titleSettings={{
          text: 'Crude Oil Production of Non-OPEC Countries (in Million barrels per day)',
          textStyle: {
            size: '15px',
            fontWeight: '500',
            fontStyle: 'Normal',
            fontFamily: 'Segoe UI'
          }
        }}
        xAxis={{
          labels: ['Canada', 'China', 'Egypt', 'Mexico', 'Norway', 'Russia', 'UK', 'USA']
        }}
        yAxis={{
          labels: [
            '2000',
            '2001',
            '2002',
            '2003',
            '2004',
            '2005',
            '2006',
            '2007',
            '2008',
            '2009',
            '2010'
          ]
        }}
        cellSettings={{
          showLabel: false
        }}
        showTooltip={true}
        tooltipRender={this.tooltipTemplate as any}
        dataSource={this.heatmapData}
      >
        <Inject services={[Legend, Tooltip]} />
      </HeatMapComponent>
    );
  }

  tooltipTemplate(args: ITooltipEventArgs): void {
    args.content = [
      'In ' +
        args.yLabel +
        ', the ' +
        args.xLabel +
        ' produced ' +
        args.value +
        ' million barrels per day'
    ];
  }
}
ReactDOM.render(<App />, document.getElementById('heatmap'));

```

{% endtab %}

## Customize the appearance of Tooltip

The  [`fill`](../api/heatmap/tooltipSettings/#fill) and [`border`](../api/heatmap/tooltipSettings/#border) properties are used to customize the background color and border of the Tooltip respectively. The [`textStyle`](../api/heatmap/tooltipSettings/#textStyle) property in the Tooltip is used to customize the font of the tooltip text.

{% tab template= "heatmap/tooltip", sourceFiles="app/**/*.tsx", compileJsx=true%}

```typescript

import * as React from "react";
import * as ReactDOM from 'react-dom';
import { HeatMapComponent, Inject, Legend, Tooltip } from '@syncfusion/ej2-react-heatmap';

class App extends React.Component {
     heatmapData: any[] = [
    [0.72, 0.71, 0.71, 0.67, 0.72, 0.53, 0.53, 0.56, 0.58, 0.56],
    [2.28, 2.29, 2.09, 1.84, 1.64, 1.49, 1.49, 1.39, 1.32, 1.23],
    [2.02, 2.17, 2.3, 2.39, 2.36, 2.52, 2.62, 2.57, 2.57, 2.74],
    [3.21, 3.26, 3.45, 3.47, 3.42, 3.34, 3.14, 2.83, 2.64, 2.61],
    [3.22, 3.13, 3.04, 2.95, 2.69, 2.49, 2.27, 2.18, 2.06, 1.87],
    [3.3, 3.39, 3.4, 3.48, 3.6, 3.67, 3.73, 3.79, 3.79, 4.07],
    [5.8, 5.74, 5.64, 5.44, 5.18, 5.08, 5.07, 5.0, 5.35, 5.47],
    [6.91, 7.4, 8.13, 8.8, 9.04, 9.24, 9.43, 9.35, 9.49, 9.69]
  ];
  render() {
    return (
      <HeatMapComponent
        id="heatmap"
        titleSettings={{
          text: 'Crude Oil Production of Non-OPEC Countries (in Million barrels per day)',
          textStyle: {
            size: '15px',
            fontWeight: '500',
            fontStyle: 'Normal',
            fontFamily: 'Segoe UI'
          }
        }}
        xAxis={{
          labels: ['Canada', 'China', 'Egypt', 'Mexico', 'Norway', 'Russia', 'UK', 'USA']
        }}
        yAxis={{
          labels: [
            '2000',
            '2001',
            '2002',
            '2003',
            '2004',
            '2005',
            '2006',
            '2007',
            '2008',
            '2009',
            '2010'
          ]
        }}
        paletteSettings={{
          palette: [{ color: '#F0ADCE' }, { color: '#19307B' }]
        }}
        cellSettings={{
          showLabel: false
        }}
        tooltipSettings={{
          fill: '#696295',
          textStyle: {
            color: '#FFFFFF',
            size: '12px'
          },
          border: {
            width: 2,
            color: '#F0C27B'
          }
        }}
        showTooltip={true}
        tooltipRender={this.tooltipTemplate as any}
        dataSource={this.heatmapData}
      >
        <Inject services={[Legend, Tooltip]} />
      </HeatMapComponent>
    );
  }

  tooltipTemplate(args: ITooltipEventArgs): void {
    args.content = [
      'In ' +
        args.yLabel +
        ', the ' +
        args.xLabel +
        ' produced ' +
        args.value +
        ' million barrels per day'
    ];
  }
}
ReactDOM.render(<App />, document.getElementById('heatmap'));

```

{% endtab %}

>Note: To use tooltip feature, we need to inject `Tooltip` module into the `services`.
