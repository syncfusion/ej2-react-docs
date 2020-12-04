---
title: "Protection"
component: "Spreadsheet"
description: "This section helps you to protect and unprotect the spreadsheet."
---

# Protection

Sheet protection helps you to prevent the users from modifying the data in the spreadsheet.

## Protect Sheet

Protect sheet feature helps you to prevent the unknown users from accidentally changing, editing, moving, or deleting data in a spreadsheet.
You can use the [`isProtected`](../api/spreadsheet/#isProtected) property to enable or disable the Protecting functionality.

> * The default value for `isProtected` property is `false`.

By default in protected sheet, selecting, formatting, inserting, deleting functionalities are disabled. To enable some of the above said functionalities
the `protectSettings` options are used in a protected spreadsheet.

The available `protectSettings` options in spreadsheet are,

| Options | Uses |
|-----|------|
| `Select Cells` | Used to perform Cell Selection. |
| `Format Cells` | Used to perform Cell formatting. |
| `Format Rows` | Used to perform Row formatting. |
| `Format Columns` | Used to perform Column formatting. |
| `Insert Link` | Used to perform Hyperlink Insertions. |

> * The default value for all `protectSettings` options are `false`.

By default, the `Protect Sheet` module is injected internally into the Spreadsheet to perform sheet protection function.

### User Interface

In the active Spreadsheet, the sheet protection can be done by any of the following ways:

* Select the Protect Sheet item in the Ribbon toolbar under the Data Tab, and then select your desired options.
* Right-click the sheet tab, select the Protect Sheet item in the context menu, and then select your desired options.
* Use the [`protectSheet()`](../api/spreadsheet/#protectSheet) method programmatically.

The following code example shows `Protect Sheet` functionality in the Spreadsheet control.

{% tab template="spreadsheet/protect-sheet", sourceFiles="app/**/*.tsx,index.html", iframeHeight="450px", isDefaultActive=true, compileJsx=true %}

```tsx

import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { SpreadsheetComponent, SheetsDirective, SheetDirective, RangesDirective, RowsDirective, RowDirective, CellDirective, CellsDirective, protectSheet, ProtectSettings } from '@syncfusion/ej2-react-spreadsheet';
import { RangeDirective, ColumnsDirective, ColumnDirective} from '@syncfusion/ej2-react-spreadsheet';
import { budgetData, salaryData } from './datasource';

export default class App extends React.Component<{}, {}> {
       public spreadsheet: SpreadsheetComponent;
       public protectSettings = {selectCells: true};
       public dataBound(): void{
        this.spreadsheet.cellFormat({ fontWeight: 'bold', textAlign: 'center' }, 'A1:D1');
        this.spreadsheet.cellFormat({ fontWeight: 'bold'}, 'A11:D11');
    };
  
     render() {
        return  ( <div> <SpreadsheetComponent
                        ref={(ssObj) => { this.spreadsheet = ssObj }} dataBound={this.dataBound.bind(this)} >
                        <SheetsDirective>
                            <SheetDirective name={"Budget"} isProtected={true} protectSettings={this.protectSettings}>
                                <RangesDirective>
                                    <RangeDirective dataSource={budgetData}></RangeDirective>
                                </RangesDirective>
                                <ColumnsDirective>
                                    <ColumnDirective width={100}></ColumnDirective>
                                    <ColumnDirective width={100}></ColumnDirective>
                                    <ColumnDirective width={100}></ColumnDirective>
                                    <ColumnDirective width={100}></ColumnDirective>
                                </ColumnsDirective>
                            </SheetDirective>
                            <SheetDirective name={"Salary"}>
                                <RangesDirective>
                                    <RangeDirective dataSource={salaryData}></RangeDirective>
                                </RangesDirective>
                                <ColumnsDirective>
                                    <ColumnDirective width={100}></ColumnDirective>
                                    <ColumnDirective width={100}></ColumnDirective>
                                    <ColumnDirective width={100}></ColumnDirective>
                                    <ColumnDirective width={100}></ColumnDirective>
                                </ColumnsDirective>
                            </SheetDirective>
                        </SheetsDirective>
                    </SpreadsheetComponent> </div>);
    }
}
ReactDOM.render(<App />, document.getElementById('root'));


```

{% endtab %}

## Unprotect Sheet

Unprotect sheet is used to enable all the functionalities that are already disabled in a protected spreadsheet.

### User Interface

In the active Spreadsheet, the sheet Unprotection can be done by any of the following ways:

* Select the `Unprotect Sheet` item in the Ribbon toolbar under the Data Tab.
* Right-click the sheet tab, select the `Unprotect Sheet` item in the context menu.
* Use the [`unprotectSheet()`](../api/spreadsheet/#unprotectSheet) method programmatically.

## Unlock the particular cells in the protected sheet

In protected spreadsheet, to make some particular cell or range of cells are editable, you can use [`lockCells()`](../api/spreadsheet/#lockCells) method, with the parameter `range` and `isLocked` property as false.

{% tab template="spreadsheet/unlock-cells", sourceFiles="app/**/*.tsx,index.html", iframeHeight="450px", isDefaultActive=true, compileJsx=true %}

```tsx
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { SpreadsheetComponent, SheetsDirective, SheetDirective, RangesDirective, RowsDirective, RowDirective, CellDirective, CellsDirective, protectSheet, ProtectSettings } from '@syncfusion/ej2-react-spreadsheet';
import { RangeDirective, ColumnsDirective, ColumnDirective} from '@syncfusion/ej2-react-spreadsheet';
import { budgetData, salaryData } from './datasource';
import { DialogComponent, ButtonPropsModel } from '@syncfusion/ej2-react-popups';

export default class App extends React.Component<{}, {}> {
       public spreadsheet: SpreadsheetComponent;
       public dialogObj: DialogComponent;
       public protectSettings = {selectCells: true};
       public btn: ButtonPropsModel[] =[ {click: this.lockCells.bind(this),
        buttonModel: { content: 'Ok', isPrimary: true }}];
       public dataBound(): void{
        this.spreadsheet.cellFormat({ fontWeight: 'bold', textAlign: 'center' }, 'A1:D1');
        this.spreadsheet.cellFormat({ fontWeight: 'bold'}, 'A11:D11');
    };
       public lockCells(): void {
        this.spreadsheet.lockCells('A1:F3', false);
        this.dialogObj.hide();
    }
    public showDlg(): void {
        this.dialogObj.show();
    }
     render() {
        return  ( <div> <button className='e-btn' onClick={ this.showDlg.bind(this) }>Unlock cells</button>
        <SpreadsheetComponent
                        ref={(ssObj) => { this.spreadsheet = ssObj }} dataBound={this.dataBound.bind(this)} >
                        <SheetsDirective>
                            <SheetDirective name={"Budget"} isProtected={true} protectSettings={this.protectSettings}>
                                <RangesDirective>
                                    <RangeDirective dataSource={budgetData}></RangeDirective>
                                </RangesDirective>
                                <ColumnsDirective>
                                    <ColumnDirective width={100}></ColumnDirective>
                                    <ColumnDirective width={100}></ColumnDirective>
                                    <ColumnDirective width={100}></ColumnDirective>
                                    <ColumnDirective width={100}></ColumnDirective>
                                </ColumnsDirective>
                            </SheetDirective>
                            <SheetDirective name={"Salary"}>
                                <RangesDirective>
                                    <RangeDirective dataSource={salaryData}></RangeDirective>
                                </RangesDirective>
                                <ColumnsDirective>
                                    <ColumnDirective width={100}></ColumnDirective>
                                    <ColumnDirective width={100}></ColumnDirective>
                                    <ColumnDirective width={100}></ColumnDirective>
                                    <ColumnDirective width={100}></ColumnDirective>
                                </ColumnsDirective>
                            </SheetDirective>
                        </SheetsDirective>
                    </SpreadsheetComponent>
                    <DialogComponent ref={(dlgObj) => { this.dialogObj = dlgObj }} header={'Spreadsheet'} target={document.getElementById('spreadsheet')} content={'"A1:F3" range of cells has been unlocked.'}
                    showCloseIcon={true} isModal={true} visible={false} width={'500px'} buttons={this.btn}>
                        </DialogComponent> </div>);
    }
}
ReactDOM.render(<App />, document.getElementById('root'));


```

{% endtab %}

## See Also

* [Hyperlink](./link)