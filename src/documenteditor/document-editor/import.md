---
title: "Import"
component: "DocumentEditor"
description: "Learn how to import SFDT and word documents in React document editor using supported APIs."
---

# Import

In Document Editor, the documents are stored in its own format called **Syncfusion Document Text (SFDT)**.

The following example shows how to open SFDT data in Document Editor.

{% tab template="document-editor/import" compileJsx=true %}

```typescript
import * as ReactDOM from 'react-dom';
import * as React from 'react';
import {
    DocumentEditorComponent, DocumentEditor
} from '@syncfusion/ej2-react-documenteditor';

export class Default extends React.Component<{}, {}> {
    public documenteditor: DocumentEditorComponent;

    public componentDidMount(): void {
        let sfdt: string = `{
        "sections": [
        {
            "blocks": [
                {
                    "inlines": [
                        {
                            "characterFormat": {
                                "bold": true,
                                "italic": true
                            },
                            "text": "Hello World"
                        }
                    ]
                }
            ],
            "headersFooters": {
            }
        }
    ]
    }`;

    setTimeout(()=>{
        this.documenteditor.open(sfdt);
    });
    }

    render() {
        return (
            <DocumentEditorComponent id="container" ref={(scope) => { this.documenteditor = scope; }} />
        );
    }
}
ReactDOM.render(<Default />, document.getElementById('sample'));
```

{% endtab %}

## Import document from local machine

The following example shows how to import document from local machine.

{% tab template="document-editor/import" compileJsx=true %}

```typescript
import * as ReactDOM from 'react-dom';
import * as React from 'react';
import {
  DocumentEditorComponent,
  DocumentEditor,
} from '@syncfusion/ej2-react-documenteditor';

export class Default extends React.Component<{}, {}> {
  public documenteditor: DocumentEditorComponent;

  onImportClick(): void {
    document.getElementById('file_upload').click();
  }

  onFileChange(e: any): void {
    if (e.target.files[0]) {
      let file = e.target.files[0];
      if (file.name.substr(file.name.lastIndexOf('.')) === '.sfdt') {
        let fileReader: FileReader = new FileReader();
        fileReader.onload = (e: any) => {
          let contents: string = e.target.result;
          let proxy:any=this;
          proxy.documenteditor.open(contents);
        };
        fileReader.readAsText(file);
        this.documenteditor.documentName = file.name.substr(
          0,
          file.name.lastIndexOf('.')
        );
      }
    }
  }
  render() {
    return (
      <div>
      <input type='file' id='file_upload' accept='.sfdt' onChange={this.onFileChange.bind(this)}/>
        <button onClick={this.onImportClick.bind(this)}>Import</button>
        <DocumentEditorComponent
          id="container"
          ref={scope => {
            this.documenteditor = scope;
          }}
        />
      </div>
    );
  }
}
ReactDOM.render(<Default />, document.getElementById('sample'));


```

{% endtab %}

## Convert word documents into SFDT

You can convert word documents into SFDT format using the .NET Standard library “Syncfusion.EJ2.DocumentEditor” by the web API service implementation. This library helps you to convert word documents (.dotx,.docx,.docm,.dot,.doc), rich text format documents (.rtf), and text documents (.txt) into SFDT format. Refer to the following example.

{% tab compileJsx=true%}

```typescript
import * as ReactDOM from 'react-dom';
import * as React from 'react';
import {
  DocumentEditorComponent,
  DocumentEditor,
} from '@syncfusion/ej2-react-documenteditor';

export class Default extends React.Component<{}, {}> {
  public documenteditor: DocumentEditorComponent;

  onImportClick(): void {
    document.getElementById('file_upload').click();
  }

  onFileChange(e: any): void {
     if (e.target.files[0]) {
        let file = e.target.files[0];
        if (file.name.substr(file.name.lastIndexOf('.')) !== '.sfdt') {
            loadFile(file);
        }
    }
  }

  loadFile(file: File): void {
    let ajax: XMLHttpRequest = new XMLHttpRequest();
    ajax.open('POST', 'https://localhost:4000/api/documenteditor/Import', true);
    ajax.onreadystatechange = () => {
      if (ajax.readyState === 4) {
        if (ajax.status === 200 || ajax.status === 304) {
          // open SFDT text in document editor
          documenteditor.open(ajax.responseText);
        }
      }
    };
    let formData: FormData = new FormData();
    formData.append('files', file);
    ajax.send(formData);
  }
  render() {
    return (
      <div>
        <input type="file" id="file_upload" accept=".dotx,.docx,.docm,.dot,.doc,.rtf,.txt,.xml,.sfdt" onChange={this.onFileChange.bind(this)} />
        <button onClick={this.onImportClick.bind(this)}>Import</button>
        <DocumentEditorComponent id="container" ref={scope => {
            this.documenteditor = scope; }} />
      </div>
    );
  }
}
ReactDOM.render(<Default />, document.getElementById('sample'));

```

{% endtab %}

Here’s how to handle the server-side action for converting word document in to SFDT.

```csharp
[AcceptVerbs("Post")]
public string Import(IFormCollection data)
{
    if (data.Files.Count == 0)
        return null;
    Stream stream = new MemoryStream();
    IFormFile file = data.Files[0];
    int index = file.FileName.LastIndexOf('.');
    string type = index > -1 && index < file.FileName.Length - 1 ?
        file.FileName.Substring(index) : ".docx";
    file.CopyTo(stream);
    stream.Position = 0;

    WordDocument document = WordDocument.Load(stream, GetFormatType(type.ToLower()));
    string sfdt = Newtonsoft.Json.JsonConvert.SerializeObject(document);
    document.Dispose();
    return sdft;
}

internal static FormatType GetFormatType(string format)
{
    if (string.IsNullOrEmpty(format))
        throw new NotSupportedException("EJ2 DocumentEditor does not support this file format.");
    switch (format.ToLower()) {
        case ".dotx":
        case ".docx":
        case ".docm":
        case ".dotm":
            return FormatType.Docx;
        case ".dot":
        case ".doc":
            return FormatType.Doc;
        case ".rtf":
            return FormatType.Rtf;
        case ".txt":
            return FormatType.Txt;
        case ".xml":
            return FormatType.WordML;
        default:
            throw new NotSupportedException("EJ2 DocumentEditor does not support this file format.");
    }
}

```

## See Also

* [Feature modules](../document-editor/feature-module/)