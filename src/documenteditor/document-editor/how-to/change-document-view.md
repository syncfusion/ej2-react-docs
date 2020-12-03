---
title: "How to"
component: "DocumentEditor"
description: "Learn how to change the document view to web layout and print view in document editor."
---

# Change document view

## How to change the document view in DocumentEditor component

DocumentEditor allows you to change the view to web layout and print using the [`layoutType`](../../api/document-editor#layouttype) property with the supported [`LayoutType`](../../api/document-editor/layouttype/).

```typescript
 <DocumentEditorComponent id="container" layoutType={'Continuous'} />
```

>Note: Default value of [`layoutType`](../../api/document-editor#layouttype) in DocumentEditor component is [`Pages`](../../api/document-editor/layoutType/).

## How to change the document view in DocumentEditorContainer component

DocumentEditorContainer component allows you to change the view to web layout and print using the [`layoutType`](../../api/document-editor-container#layouttype) property with the supported [`LayoutType`](../../api/document-editor/layouttype/).

```typescript
<DocumentEditorContainerComponent id="container" layoutType={'Continuous'} enableToolbar={true}/>
```

>Note: Default value of [`layoutType`](../../api/document-editor-container#layouttype) in DocumentEditorContainer component is [`Pages`](../../api/document-editor/layoutType/).