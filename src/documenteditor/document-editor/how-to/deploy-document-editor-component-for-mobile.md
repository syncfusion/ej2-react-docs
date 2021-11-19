---
title: "How to deploy Document Editor for Mobile"
component: "DocumentEditor"
description: "Learn how to deploy Document Editor on a Mobile-Friendly Web page, such as to switch automatically in ready-only and full-page views when opened in mobile browsers."
---

# Deploy Document Editor component for Mobile

## Document editor component for Mobile

At present, Document editor component is not responsive for mobile, and we haven't ensured the editing functionalities in mobile browsers. Whereas it works properly as a document viewer in mobile browsers.

Hence, it is recommended to switch the Document editor component as read-only in mobile browsers. Also, invoke [`fitPage`](../../api/document-editor/#fitpage/) method with `FitPageWidth` parameter in document change event, such as to display one full page by adjusting the zoom factor.

The following example code illustrates how to deploy Document Editor component for Mobile.

```typescript

//Initialize Document Editor Container component.
import { DocumentEditorContainer,Toolbar } from '@syncfusion/ej2-documenteditor';
import * as ReactDOM from 'react-dom';
import * as React from 'react';

DocumentEditorContainer.Inject(Toolbar);
export class Default extends React.Component<{}, {}> {
  hosturl = 'https://ej2services.syncfusion.com/production/web-services/api/documenteditor/';

  onDocumentChange() {
    let proxy = this;
    //To detect the device
    let isMobileDevice = /Android|Windows Phone|webOS/i.test(navigator.userAgent);

    if (isMobileDevice) {
      proxy.container.restrictEditing = true;
      setTimeout(() => {
        proxy.container.documentEditor.fitPage("FitPageWidth");
      }, 50);
    }
    else {
      proxy.container.restrictEditing = false;
    }
  }


  render() {
    return (
      <div className="App">
        <DocumentEditorContainerComponent id="container" ref={(scope) => { this.container = scope; }} style={{ 'height': '590px' }} enableToolbar={true} documentChange={this.onDocumentChange.bind(this)} serviceUrl={this.hosturl} height={'590px'}/>
      </div>
    );
  }
}

ReactDOM.render(<Default />, document.getElementById('sample'));

```

You can download the complete working example from this [GitHub location](https://github.com/SyncfusionExamples/Deploy-Document-Editor-in-Mobile-Friendly-Web-page/)

>Note: You can use the [`restrictEditing`](../../api/document-editor-container#restrictediting) in DocumentEditorContainer and [`isReadOnly`](../../api/document-editor/#isreadonly) in DocumentEditor based on your requirement to change component to read only mode.