---
title: "Getting Started"
component: "Spinner"
description: "This example demonstrates how to create the Essential JS 2 Spinner control with its basic features in React application."
---

# Getting Started

Initialize the Spinner using `createSpinner` method.

You can show/hide Spinner by using `showSpinner` and `hideSpinner` methods accordingly. You need to set target to render based on specific target.

The following steps explains you on how to create and how to show/hide your Spinner.

* Import the `createSpinner` method from `ej2-popups` library into your file as shown in below.

```typescript
import { createSpinner } from '@syncfusion/ej2-popups';
```

* Show and hide this spinner by using `showSpinner` and `hideSpinner` methods for loading in your page and import them in your file as shown in below.

```typescript
import { showSpinner, hideSpinner } from '@syncfusion/ej2-popups';
```

## Create the Spinner globally

The Spinner can be render globally in a page using public exported functions of the `ej2-popups` package.

{% tab template="spinner/intro",  compileJsx=true, isDefaultActive=true %}

```typescript

import { createSpinner, showSpinner, hideSpinner } from '@syncfusion/ej2-popups';

//createSpinner() method is used to create spinner

 createSpinner({

  // Specify the target for the spinner to show

        target: document.getElementById('container')

    });

// showSpinner() will make the spinner visible

 showSpinner(document.getElementById('container'));

setInterval(function(){

  // hideSpinner() method used hide spinner
  hideSpinner(document.getElementById('container'));

}, 100000);


```

{% endtab %}