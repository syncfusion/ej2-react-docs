---
title: " Open Street Maps in React Maps control | Syncfusion "

component: "Maps"

description: "Learn here all about Open Street Maps of Syncfusion React Maps control and more."
---

# Open Street Maps in React Maps control

The OpenStreetMap (OSM) is the online map provider built by a community of developers; it is free to use under an open license. It allows to view geographical data in a collaborative way from anywhere on the earth. The OSM map provides small tile images based on our requests and combines those images into a single image to display the map area in the Maps component.

## Adding OpenStreetMap

The OSM map can be rendered using by setting the [`layerType`](../api/maps/layerSettingsModel/#layertype) property value as "**OSM**".

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
//tslint:disable
import { world_map } from 'world-map.ts';
import { usa_map } from 'usa.ts'
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="maps">
                <LayersDirective>
                    <LayerDirective layerType='OSM' />
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);

```

{% endtab %}

### Changing the tile server of the OpenStreetMap

The OSM tile server can be changed by setting the tile URL in the [`urlTemplate`](../api/maps/layerSettingsModel/#urltemplate) property. For more details about the OSM tile server, refer [here](https://wiki.openstreetmap.org/wiki/Tiles).

## Zooming and panning

The OSM maps layer can be zoomed and panned. Zooming helps to get a closer look at a particular area on a map for in-depth analysis. Panning helps to move a map around to focus the targeted area.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
//tslint:disable
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, Zoom } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="maps" zoomSettings = { { enable: true, toolbars: ['Zoom', 'ZoomIn', 'ZoomOut', 'Pan', 'Reset']} }>
                <LayersDirective>
                    <LayerDirective layerType='OSM' />
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);

```

{% endtab %}

## Adding markers and navigation line

Markers can be added to the layers of OSM maps by setting the corresponding location's coordinates of latitude and longitude using [`markerSettings`](../api/maps/layerSettingsModel/#markersettings) property. Navigation lines can be added on top of an OSM maps layer for highlighting a path among various places by setting the corresponding location's coordinates of latitude and longitude in the [`navigationLineSettings`](../api/maps/layerSettingsModel/#navigationlinesettings) property.

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
//tslint:disable
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, NavigationLineDirective, LayerDirective, Zoom, MarkersDirective, NavigationLine, NavigationLinesDirective, MarkerDirective, Marker, Inject } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="maps" zoomSettings = { { zoomFactor: 4 } } centerPosition = {{ latitude: 29.394708, longitude: -94.954653}}>
            <Inject services={[Marker, NavigationLine]} />
                <LayersDirective>
                    <LayerDirective layerType='OSM'>
                        <MarkersDirective>
                            <MarkerDirective visible={true}
                                            height={25}
                                            width={15}
                                            dataSource={[
                                                {
                                                    latitude: 34.060620,
                                                    longitude: -118.330491,
                                                    name: "California"
                                                },
                                                {
                                                    latitude: 40.724546,
                                                    longitude: -73.850344,
                                                    name: "New York"
                                                }
                                            ]}
                                        >
                            </MarkerDirective>
                        </MarkersDirective>
                        <NavigationLinesDirective>
                            <NavigationLineDirective visible={true}
                                                     latitude={[34.060620, 40.724546]}
                                                     longitude={[-118.330491,-73.850344]}
                                                     color="blue"
                                                     angle={90}
                                                     width={5} />
                        </NavigationLinesDirective>
                    </LayerDirective>
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);

```

{% endtab %}

## Sublayer

Any GeoJSON shape can be rendered as a sublayer on top of the OSM maps layer for highlighting a particular continent or country in OSM maps by adding another layer and specifying the [`type`](../api/maps/layerSettingsModel/#type) property of maps layer to "**SubLayer**".

{% tab template="maps/default-map", compileJsx=true, sourceFiles="app/**/*.tsx" %}

```tsx
//tslint:disable
import { usa_map } from 'usa.ts';
import * as React from "react";
import * as ReactDOM from "react-dom";
import { MapsComponent, LayersDirective, LayerDirective, Zoom } from '@syncfusion/ej2-react-maps';

ReactDOM.render(
            <MapsComponent id="maps">
                <LayersDirective>
                    <LayerDirective layerType='OSM' />
                    <LayerDirective shapeData= {usa_map}
                                    type= 'SubLayer'
                                    shapeSettings= {{
                                        fill: 'blue'
                                    }}

                    />
                </LayersDirective>
            </MapsComponent>,
document.getElementById("maps") as HTMLElement
);

```

{% endtab %}