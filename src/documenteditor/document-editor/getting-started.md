---
title: "Getting Started"
component: "DocumentEditor"
description: "Learn how to get started using React document editor component through simple steps."
---

# Getting Started

This section explains the steps to create a Word document editor within your application and demonstrates the basic usage of the DocumentEditor component.

## Dependencies

Following is the list of minimum dependencies required to use the documenteditor.

```javascript
|-- @syncfusion/ej2-react-documenteditor
    |-- @syncfusion/ej2-react-base
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-build
    |-- @syncfusion/ej2-buttons
    |-- @syncfusion/ej2-compression
    |-- @syncfusion/ej2-data
    |-- @syncfusion/ej2-dropdowns
    |-- @syncfusion/ej2-file-utils
    |-- @syncfusion/ej2-inputs
    |-- @syncfusion/ej2-lists
    |-- @syncfusion/ej2-navigations
    |-- @syncfusion/ej2-popups
    |-- @syncfusion/ej2-splitbuttons
    |-- @syncfusion/ej2-documenteditor
    |-- @syncfusion/ej2-charts
```

## Setup for Local Development

You can use [`create-react-app`](https://github.com/facebookincubator/create-react-app/) to setup the applications.
To install `create-react-app` run the following command.

```sh
npm install -g create-react-app
```

* To setup basic `React` sample use following commands.

<div class='tsx'>

```sh
create-react-app quickstart --scripts-version=react-scripts-ts

cd quickstart

npm install

```

</div>

<div class='jsx'>

```bash

create-react-app quickstart

cd quickstart

npm install

```

</div>

## Adding Syncfusion packages

All the available Essential JS 2 packages are published in [`npmjs.com`](https://www.npmjs.com/~syncfusionorg/) public registry.
You can choose the component that you want to install.

To install Documenteditor component, use the following command

```sh
npm install @syncfusion/ej2-react-documenteditor --save
```

## Adding CSS reference

 Add DocumentEditor component's styles as given below in `src/App.css`.

```css
@import '../../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-inputs/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-popups/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-lists/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-navigations/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';
@import "../../node_modules/@syncfusion/ej2-react-documenteditor/styles/material.css";
```

> To refer `App.css` in the application then import it in the `src/App.tsx` file.

## Adding Component

You can add `DocumentEditorContainer` Component with  predefined toolbar and properties pane options or `DocumentEditor` component with customize options.

## DocumentEditor component

DocumentEditor Component is used to create , view and edit word documents. In this , you can customize the UI options based on your requirements to modify the document.

### Adding DocumentEditor component

Now, you can start adding DocumentEditor component in the application. For getting started, add the DocumentEditor component in `src/App.tsx` file using following code.

Add the below code in the `src/App.tsx` to initialize the DocumentEditor.

{% tab compileJsx=true%}

```tsx
import * as React from 'react';
import { DocumentEditorComponent, Print, SfdtExport, WordExport, TextExport, Selection, Search, Editor, ImageResizer, EditorHistory, ContextMenu, OptionsPane, HyperlinkDialog, TableDialog, BookmarkDialog, TableOfContentsDialog, PageSetupDialog, StyleDialog, ListDialog, ParagraphDialog, BulletsAndNumberingDialog, FontDialog, TablePropertiesDialog, BordersAndShadingDialog, TableOptionsDialog, CellOptionsDialog, StylesDialog } from '@syncfusion/ej2-react-documenteditor';
DocumentEditorComponent.Inject(Print, SfdtExport, WordExport, TextExport, Selection, Search, Editor, ImageResizer, EditorHistory, ContextMenu, OptionsPane, HyperlinkDialog, TableDialog, BookmarkDialog, TableOfContentsDialog, PageSetupDialog, StyleDialog, ListDialog, ParagraphDialog, BulletsAndNumberingDialog, FontDialog, TablePropertiesDialog, BordersAndShadingDialog, TableOptionsDialog, CellOptionsDialog, StylesDialog);
export default class App extends React.Component {
    render() {
        return (<DocumentEditorComponent id="container" serviceUrl="https://ej2services.syncfusion.com/production/web-services/api/documenteditor/" isReadOnly={false} enablePrint={true} enableSelection={true} enableEditor={true} enableEditorHistory={true} enableContextMenu={true} enableSearch={true} enableOptionsPane={true} enableBookmarkDialog={true} enableBordersAndShadingDialog={true} enableFontDialog={true} enableTableDialog={true} enableParagraphDialog={true} enableHyperlinkDialog={true} enableImageResizer={true} enableListDialog={true} enablePageSetupDialog={true} enableSfdtExport={true} enableStyleDialog={true} enableTableOfContentsDialog={true} enableTableOptionsDialog={true} enableTablePropertiesDialog={true} enableTextExport={true} enableWordExport={true}/>);
    }
}

```

{% endtab %}

> The DocumentEditor requires server-side interactions for the following operations:
>
> * Paste with formatting
> * Restrict editing
> * Spellcheck
>
> Refer to this [link](https://github.com/SyncfusionExamples/EJ2-DocumentEditor-WebServices) to configure the web service and set the [serviceUrl](../api/document-editor#serviceurl).

### Run the DocumentEditor application

The [`create-react-app`](https://github.com/facebookincubator/create-react-app/) will pre-configure the project to compile and
run the application in browser. Use the following command to run the application.

```sh
npm start
```

Documenteditor output will be displayed as follows.

{% tab template="document-editor/base" compileJsx=true %}

```tsx

import * as ReactDOM from 'react-dom';
import * as React from 'react';

import {
    DocumentEditorComponent, DocumentEditor, RequestNavigateEventArgs, ViewChangeEventArgs,
    Print, SfdtExport, WordExport, TextExport, Selection, Search, Editor, ImageResizer, EditorHistory,
    ContextMenu, OptionsPane, HyperlinkDialog, TableDialog, BookmarkDialog, TableOfContentsDialog,
    PageSetupDialog, StyleDialog, ListDialog, ParagraphDialog, BulletsAndNumberingDialog, FontDialog,
    TablePropertiesDialog, BordersAndShadingDialog, TableOptionsDialog, CellOptionsDialog, StylesDialog
} from '@syncfusion/ej2-react-documenteditor';


DocumentEditorComponent.Inject(Print, SfdtExport, WordExport, TextExport, Selection, Search, Editor, ImageResizer, EditorHistory, ContextMenu, OptionsPane, HyperlinkDialog, TableDialog, BookmarkDialog, TableOfContentsDialog, PageSetupDialog, StyleDialog, ListDialog, ParagraphDialog, BulletsAndNumberingDialog, FontDialog, TablePropertiesDialog, BordersAndShadingDialog, TableOptionsDialog, CellOptionsDialog, StylesDialog);
export class Default extends React.Component<{}, {}> {
  render() {
    return (
        <DocumentEditorComponent id="container" serviceUrl="https://ej2services.syncfusion.com/production/web-services/api/documenteditor/" isReadOnly={false} enablePrint={true}
        enableSelection={true} enableEditor={true} enableEditorHistory={true}
        enableContextMenu={true} enableSearch={true} enableOptionsPane={true}
        enableBookmarkDialog={true} enableBordersAndShadingDialog={true} enableFontDialog={true} enableTableDialog={true} enableParagraphDialog={true} enableHyperlinkDialog={true} enableImageResizer={true} enableListDialog={true}
        enablePageSetupDialog={true} enableSfdtExport={true}
        enableStyleDialog={true} enableTableOfContentsDialog={true}
        enableTableOptionsDialog={true} enableTablePropertiesDialog={true}
        enableTextExport={true} enableWordExport={true} />
    );
  }
}
ReactDOM.render(<Default />, document.getElementById('sample'));

```

{% endtab %}

## DocumentEditorContainer component

DocumentEditorContainer Component is also used to create, view and edit word document. But here, you can use predefined toolbar and properties pane to view and modify word document.

### Adding DocumentEditorContainer component

Now, you can start adding DocumentEditorContainer component in the application. For getting started, add the DocumentEditorContainer component in `src/App.tsx` file using following code.

Add the below code in the `src/App.tsx` to initialize the DocumentEditor.

{% tab compileJsx=true%}

```tsx
import * as React from 'react';
import { DocumentEditorContainerComponent, Toolbar } from '@syncfusion/ej2-react-documenteditor';
DocumentEditorContainerComponent.Inject(Toolbar);
export default class App extends React.Component {
    render() {
        return (<DocumentEditorContainerComponent id="container" style={{ 'height': '590px' }} serviceUrl="https://ej2services.syncfusion.com/production/web-services/api/documenteditor/" enableToolbar={true}/>);
    }
}

```

{% endtab %}

> The DocumentEditorContainer requires server-side interactions for the following operations:
>
> * Opening word documents
> * Paste with formatting
> * Restrict editing
> * Spellcheck
>
> Refer to this [link](https://github.com/SyncfusionExamples/EJ2-DocumentEditor-WebServices) to configure the web service and set the [serviceUrl](../api/document-editor-container#serviceurl).

### Run the DocumentEditorContainer application

The [`create-react-app`](https://github.com/facebookincubator/create-react-app/) will pre-configure the project to compile and
run the application in browser. Use the following command to run the application.

```sh
npm start
```

DocumentEditorContainer output will be displayed as follows.

{% tab template="document-editor/base" compileJsx=true %}

```typescript

import * as ReactDOM from 'react-dom';
import * as React from 'react';
import {
    DocumentEditorContainerComponent,Toolbar
} from '@syncfusion/ej2-react-documenteditor';

DocumentEditorContainerComponent.Inject(Toolbar);
export class Default extends React.Component<{}, {}> {
  render() {
    return (
    <DocumentEditorContainerComponent id="container" serviceUrl="https://ej2services.syncfusion.com/production/web-services/api/documenteditor/" style={{ 'height': '590px' }}  enableToolbar={true} />);
  }
}
ReactDOM.render(<Default />, document.getElementById('sample'));

```

{% endtab %}
