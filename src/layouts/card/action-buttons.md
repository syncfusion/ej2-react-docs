---
title: "Action Buttons"
component: "Card"
description: "This section explains how to customizes the card using action buttons and changes the vertical or horizontal alignment of the card element."
---

# Action Buttons

You can include Action buttons within the Card and customize them. Action button is a `div`
element with `e-card-actions` class followed by button tag or anchor tag within the card root element.

* For adding action buttons you can create button or anchor tag with `e-card-btn` class within the card action element.

```html
    <div className = "e-card">
        <div className="e-card-actions">
            <button className="e-card-btn"></button>
            <a href="#"></a>
        </div>
    </div>
```

## Vertical

By default, action buttons positioned in horizontal alignment , and also it can be aligned to show in vertical alignment by adding
`e-card-vertical` class.

```html
    <div className = "e-card">
        <div className="e-card-actions e-card-vertical">
            <button className="e-card-btn">More</button>
            <a href="#">Share</a>
        </div>
    </div>
```

{% tab template="card/card_action_btn", isDefaultActive=true, compileJsx=true  %}

```typescript
import * as React from "react";
import * as ReactDOM from "react-dom";

export default class ReactApp extends React.Component<{}, {}> {
  public render() {
    return (
      <div>
        <div id="sample">
          <div className="e-card">
            <div className="e-card-header-title">Eiffel Tower</div>
            <div className="e-card-content">
              The Eiffel Tower is acknowledged as the universal symbol of Paris and France.
            </div>
            <div className="e-card-actions">
              <button className="e-card-btn">
                <img src='./fav.png' title="Bookmark" />
              </button>
              <button className="e-card-btn">
                <img src='./like.png' title="Like" />
              </button>
              <button className="e-card-btn">
                <img src='./share.png' title="Share" />
              </button>
            </div>
          </div>
        </div>
        <div id="sample">
          <div className="e-card">
            <div className="e-card-header-title">Eiffel Tower</div>
            <div className="e-card-content">
              The Eiffel Tower is acknowledged as the universal symbol of Paris and France.
                </div>
            <div className="e-card-actions e-card-vertical">
              <button className="e-card-btn">More</button>
              <a href="#">Share</a>
            </div>
          </div>
        </div>
      </div>
    );
  }
}
ReactDOM.render(<ReactApp />, document.getElementById("element"));
```

{% endtab %}

## See Also

* [How to integrate other component inside the card](./how-to/integrate-other-component-inside-the-card/)
