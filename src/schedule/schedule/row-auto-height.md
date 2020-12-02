# Row Auto Height

By default, the height of the Scheduler rows in Timeline views are static and therefore, when the same time range holds multiple overlapping appointments, a `+n more` text indicator will be displayed. With this feature enabled, you can now view all the overlapping appointments present in those specific time range by auto-adjusting the row height based on the presence of the appointments count, instead of displaying the `+n more` text indicators.

To enable auto row height adjustments on Scheduler Timeline views and Month view, set `true` to the `rowAutoHeight` property whose default value is `false`.

> This auto row height adjustment is applicable only on all the Timeline views as well as on the calendar Month view.

Now, let's see how it works on those applicable views with examples.

## Calendar month view

By default, the rows of the calendar Month view can hold only the limited appointments count based on its row height, and the rest of the overlapping appointments are indicated with a `+n more` text indicator. The following example shows how the month view row auto-adjusts based on the number of appointments count, when this `RowAutoHeight` feature is enabled.

{% tab template="schedule/local-data", iframeHeight="588px", compileJsx=true %}

```tsx
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import {
  ScheduleComponent, Month, Inject,
  ViewsDirective, ViewDirective} from '@syncfusion/ej2-react-schedule';
import { scheduleData } from './datasource';
import { extend } from '@syncfusion/ej2-base';

class App extends React.Component<{}, {}>{
    private data: Object[] = extend([], scheduleData, null, true) as Object[];
    render() {
    return <ScheduleComponent  width= '100%' height='550px' selectedDate= {new Date(2018, 1, 15)} eventSettings= { { dataSource: this.data } } rowAutoHeight= { true }>
            <ViewsDirective>
              <ViewDirective option='Month' />
            </ViewsDirective>
            <Inject services={[Month]} />
        </ScheduleComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('schedule'));
```

{% endtab %}

## Timeline views

When the feature `RowAutoHeight` is enabled in Timeline views, the row height gets auto-adjusted based on the number of overlapping events occupied on the same time range, which is demonstrated in the following example.

{% tab template="schedule/local-data", iframeHeight="588px", compileJsx=true %}

```tsx
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import {
  ScheduleComponent, TimelineViews, Inject, TimelineMonth, Agenda,
  ViewsDirective, ViewDirective} from '@syncfusion/ej2-react-schedule';
import { scheduleData } from './datasource';
import { extend } from '@syncfusion/ej2-base';

class App extends React.Component<{}, {}>{
    private data: Object[] = extend([], scheduleData, null, true) as Object[];
    render() {
    return <ScheduleComponent  width= '100%' height='550px' selectedDate= {new Date(2018, 1, 15)} eventSettings= { { dataSource: this.data } } rowAutoHeight= { true }>
            <ViewsDirective>
              <ViewDirective option='TimelineDay' />
              <ViewDirective option='TimelineWeek' />
              <ViewDirective option='TimelineWorkWeek' />
              <ViewDirective option='TimelineMonth' />
              <ViewDirective option='Agenda' />
            </ViewsDirective>
            <Inject services={[TimelineViews, TimelineMonth, Agenda]} />
        </ScheduleComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('schedule'));
```

{% endtab %}

## Timeline views with multiple resources

The following example shows how the auto row adjustment feature works on timeline views with multiple resources.

{% tab template="schedule/local-data", iframeHeight="588px", compileJsx=true %}

```tsx
import * as ReactDOM from 'react-dom';
import * as React from 'react';
import {
    TimelineViews, ScheduleComponent, ViewsDirective,
    ViewDirective, ResourcesDirective, ResourceDirective, Inject, Resize, DragAndDrop
} from '@syncfusion/ej2-react-schedule';
import { roomData } from './datasource';
import { extend } from '@syncfusion/ej2-base';

class App extends React.Component<{}, {}>{
    private data: Object[] = extend([], roomData, null, true) as Object[];
    private ownerData: Object[] = [
        { text: 'Room A', id: 1, color: '#98AFC7' },
        { text: 'Room B', id: 2, color: '#99c68e' },
        { text: 'Room C', id: 3, color: '#C2B280' },
        { text: 'Room D', id: 4, color: '#3090C7' },
        { text: 'Room E', id: 5, color: '#95b9' },
        { text: 'Room F', id: 6, color: '#95b9c7' },
        { text: 'Room G', id: 7, color: '#deb887' },
        { text: 'Room H', id: 8, color: '#3090C7' },
        { text: 'Room I', id: 9, color: '#98AFC7' },
        { text: 'Room J', id: 10, color: '#778899' }
    ];
    render() {
    return <ScheduleComponent  width= '100%' height='550px' selectedDate= {new Date(2018, 7, 1)} eventSettings= { { dataSource: this.data } } rowAutoHeight= { true }
    eventSettings={{
        dataSource: this.data,
        fields: {
            id: 'Id',
            subject: { title: 'Summary', name: 'Subject' },
            location: { title: 'Location', name: 'Location' },
            description: { title: 'Comments', name: 'Description' },
            startTime: { title: 'From', name: 'StartTime' },
            endTime: { title: 'To', name: 'EndTime' }
        }
    }}
    group={{ enableCompactView: false, resources: ['MeetingRoom'] }} >
        <ResourcesDirective>
            <ResourceDirective field='RoomId' title='Room Type' name='MeetingRoom' allowMultiple={true}
            dataSource={this.ownerData} textField='text' idField='id' colorField='color'>
            </ResourceDirective></ResourcesDirective>
            <ViewsDirective>
              <ViewDirective option='TimelineDay' />
              <ViewDirective option='TimelineWeek' />
            </ViewsDirective>
            <Inject services={[TimelineViews, Resize, DragAndDrop]} />
        </ScheduleComponent>
    }
};
ReactDOM.render(<App />, document.getElementById('schedule'));
```

{% endtab %}
