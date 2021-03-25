---
title: "Cell Range"
component: "Spreadsheet"
description: "Learn the various operations that you can perform in range of cells of the Essential JS 2 Spreadsheet."
---

# Cell Range

A group of cells in a sheet is known as cell range.

## Wrap text

Wrap text allows you to display large content as multiple lines in a single cell. By default, the wrap text support is enabled. Use the [`allowWrap`](../api/spreadsheet/#allowwrap) property to enable or disable the wrap text support in spreadsheet.

Wrap text can be applied or removed to a cell or range of cells in the following ways,

* Using the `wrap` property in `cell`, you can enable or disable wrap text to a cell at initial load.
* Select or deselect wrap button from ribbon toolbar to apply or remove the wrap text to the selected range.
* Using the [`wrap`](../api/spreadsheet/#wrap) method, you can apply or remove the wrap text once the component is loaded.

The following code example shows the wrap text functionality in spreadsheet.

{% tab template="spreadsheet/wrap", sourceFiles="app/**/*.tsx,index.html", iframeHeight="450px", isDefaultActive=true, compileJsx=true %}

```tsx

import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { SpreadsheetComponent, SheetsDirective, SheetDirective, RangesDirective, RowsDirective, RowDirective, CellDirective, CellsDirective } from '@syncfusion/ej2-react-spreadsheet';
import { RangeDirective, ColumnsDirective, ColumnDirective} from '@syncfusion/ej2-react-spreadsheet';
import { CellStyleModel, getRangeIndexes } from '@syncfusion/ej2-react-spreadsheet';
import { data } from './datasource';
import { addClass, removeClass } from '@syncfusion/ej2-base';

export default class App extends React.Component<{}, {}> {
       public spreadsheet: SpreadsheetComponent;
       public oncreated(args): void{
        this.spreadsheet.cellFormat({ fontWeight: 'bold', textAlign: 'center' }, 'A1:H1');
        this.spreadsheet.cellFormat({ verticalAlign: 'middle' }, 'A1:H5');
        this.spreadsheet.cellFormat({ textAlign: 'center' }, 'A2:B5');
        this.spreadsheet.cellFormat({ textAlign: 'center' }, 'D2:D5');
        // To wrap the cells from E2 to E5 range
        this.spreadsheet.wrap('E2:E5');
        // To unwrap the H3 cell
        this.spreadsheet.wrap('H3', false);
    }
     render() {
        return  ( <div> <SpreadsheetComponent
                        ref={(ssObj) => { this.spreadsheet = ssObj }} created={this.oncreated.bind(this)} showFormulaBar={false} >
                        <SheetsDirective>
                            <SheetDirective name={"Movie List"}>
                             <RowsDirective>
                                 <RowDirective height={30}>
                                 </RowDirective>
                                 <RowDirective>
                                     <CellsDirective>
                                     <CellDirective index={7} wrap={true}></CellDirective>
                                     </CellsDirective>
                                     </RowDirective>
                                     <RowDirective>
                                     <CellsDirective>
                                     <CellDirective index={7} wrap={true}></CellDirective>
                                     </CellsDirective>
                                     </RowDirective>
                                     <RowDirective>
                                     <CellsDirective>
                                     <CellDirective index={7} wrap={true}></CellDirective>
                                     </CellsDirective>
                                     </RowDirective>
                                     <RowDirective>
                                     <CellsDirective>
                                     <CellDirective index={7} wrap={true}></CellDirective>
                                     </CellsDirective>
                                     </RowDirective>
                                     </RowsDirective>
                                <RangesDirective>
                                    <RangeDirective dataSource={data}></RangeDirective>
                                </RangesDirective>
                                <ColumnsDirective>
                                    <ColumnDirective width={100} index={1}></ColumnDirective>
                                    <ColumnDirective width={140}></ColumnDirective>
                                    <ColumnDirective width={90}></ColumnDirective>
                                    <ColumnDirective width={150}></ColumnDirective>
                                    <ColumnDirective width={120}></ColumnDirective>
                                    <ColumnDirective width={90}></ColumnDirective>
                                    <ColumnDirective width={180}></ColumnDirective>
                                </ColumnsDirective>
                            </SheetDirective>
                        </SheetsDirective>
                    </SpreadsheetComponent> </div>);
    }
}
ReactDOM.render(<App />, document.getElementById('root'));

```

{% endtab %}

### Limitation of Wrap text

The following features have some limitations in wrap text:

* Sorting with wrap text applied data.
* Merge with wrap text

## Merge cells

Merge cells allows users to span two or more cells in the same row or column into a single cell. When cells with multiple values are merged, top-left most cell data will be the data for the merged cell. By default, the merge cells option is enabled. Use [`allowMerge`](../api/spreadsheet/#allowmerge) property to enable or disable the merge cells option in spreadsheet.

You can merge the range of cells in the following ways,

* Set the `rowSpan` and `colSpan` property in `cell` to merge the number of cells at initial load.
* Select the range of cells and apply merge by selecting the desired option from ribbon toolbar.
* Use [`merge`](../api/spreadsheet/#merge) method to merge the range of cells, once the component is loaded.

The available merge options in spreadsheet are,

| Type | Action |
|-------|---------|
| Merge All | Combines all the cells in a range in to a single cell (default). |
| Merge Horizontally | Combines cells in a range as row-wise. |
| Merge Vertically | Combines cells in a range as column-wise. |
| UnMerge | Splits the merged cells into multiple cells. |

The following code example shows the merge cells operation in spreadsheet.

{% tab template="spreadsheet/merge", sourceFiles="app/**/*.tsx,index.html", iframeHeight="450px", isDefaultActive=true, compileJsx=true %}

```tsx


import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { SpreadsheetComponent, SheetsDirective, SheetDirective, RangesDirective, RowsDirective, RowDirective, CellsDirective, CellDirective } from '@syncfusion/ej2-react-spreadsheet';
import { RangeDirective, ColumnsDirective, ColumnDirective} from '@syncfusion/ej2-react-spreadsheet';
import { CellStyleModel, getRangeIndexes } from '@syncfusion/ej2-react-spreadsheet';
import { data } from './datasource';
import { addClass, removeClass } from '@syncfusion/ej2-base';

export default class App extends React.Component<{}, {}> {
       public spreadsheet: SpreadsheetComponent;
    public boldRight: CellStyleModel = { fontWeight: 'bold', textAlign: 'right' };
    public bold: CellStyleModel = { fontWeight: 'bold' };
     public updateCollection(): void {
        let cell = this.spreadsheet.getActiveSheet().activeCell;
        let cellIdx = getRangeIndexes(cell);
        let Element= this.spreadsheet.getCell(cellIdx[0], cellIdx[1]);
        if (!Element.classList.contains("customClass")) {
            Element.classList.add('customClass'); // To add the custom class in active cell element
            this.spreadsheet.updateUndoRedoCollection({ eventArgs: { class: 'customClass', rowIdx: cellIdx[0], colIdx: cellIdx[1], action: 'customCSS' } }); // To update the undo redo collection
        }
    }

    public oncreated(): void{
        this.spreadsheet.cellFormat({ fontWeight: 'bold', textAlign: 'center' }, 'A1:S1');
        this.spreadsheet.numberFormat('h:mm AM/PM', 'C1:S1');
        this.spreadsheet.cellFormat({ verticalAlign: 'middle' }, 'A1:S11');
        // Merging the `K4:M4` cells using method
        this.spreadsheet.merge('K4:M4');
        // Merging the 5th and 6th row cells across 11th, 12th and 13th column
        this.spreadsheet.merge('K5:M6', 'Vertically');
        // Merging the 18th and 19th column cells across 2nd, 3rd and 4th row
        this.spreadsheet.merge('N4:O6', 'Horizontally');
    }
     render() {
        return  ( <div>
             <SpreadsheetComponent
                        ref={(ssObj) => { this.spreadsheet = ssObj }} created={this.oncreated.bind(this)} showFormulaBar={false}>
                        <SheetsDirective>
                            <SheetDirective name={"Merge Cells"}>
                            <RowsDirective>
                                <RowDirective height={35}></RowDirective>
                                <RowDirective height={35}>
                                    <CellsDirective>
                                        <CellDirective index={1} rowSpan={2}></CellDirective>
                                        <CellDirective colSpan={2}></CellDirective>
                                        <CellDirective index={6} colSpan={3}></CellDirective>
                                        <CellDirective index={10} rowSpan={2} colSpan={3}></CellDirective>
                                        <CellDirective index={13} colSpan={2}></CellDirective>
                                        <CellDirective index={17} colSpan={2}></CellDirective>
                                    </CellsDirective>
                                </RowDirective>
                                <RowDirective height={35}>
                                    <CellsDirective>
                                        <CellDirective index={3} colSpan={3}></CellDirective>
                                        <CellDirective index={6} colSpan={4}></CellDirective>
                                        <CellDirective index={13} colSpan={3}></CellDirective>
                                        <CellDirective index={17} colSpan={2}></CellDirective>
                                    </CellsDirective>
                                </RowDirective>
                                <RowDirective height={35}>
                                    <CellsDirective>
                                        <CellDirective index={2} colSpan={3}></CellDirective>
                                        <CellDirective index={5} colSpan={2}></CellDirective>
                                        <CellDirective index={7} colSpan={3}></CellDirective>
                                        <CellDirective index={15} colSpan={2}></CellDirective>
                                        <CellDirective index={17} colSpan={2}></CellDirective>
                                    </CellsDirective>
                                </RowDirective>
                                <RowDirective height={35}>
                                    <CellsDirective>
                                        <CellDirective index={2} colSpan={3}></CellDirective>
                                        <CellDirective index={6} colSpan={4}></CellDirective>
                                        <CellDirective index={16} colSpan={2}></CellDirective>
                                    </CellsDirective>
                                </RowDirective>
                                <RowDirective height={35}>
                                    <CellsDirective>
                                        <CellDirective index={2} colSpan={4}></CellDirective>
                                        <CellDirective index={7} colSpan={3}></CellDirective>
                                        <CellDirective index={15} colSpan={2}></CellDirective>
                                        <CellDirective index={17} colSpan={2}></CellDirective>
                                    </CellsDirective>
                                </RowDirective>
                            </RowsDirective>
                                <RangesDirective>
                                    <RangeDirective dataSource={data}></RangeDirective>
                                </RangesDirective>
                                <ColumnsDirective>
                                    <ColumnDirective width={90}></ColumnDirective>
                                    <ColumnDirective width={150}></ColumnDirective>
                                    <ColumnDirective width={100}></ColumnDirective>
                                    <ColumnDirective width={100}></ColumnDirective>
                                    <ColumnDirective width={100}></ColumnDirective>
                                    <ColumnDirective width={100}></ColumnDirective>
                                    <ColumnDirective width={100}></ColumnDirective>
                                    <ColumnDirective width={100}></ColumnDirective>
                                    <ColumnDirective width={100}></ColumnDirective>
                                    <ColumnDirective width={100}></ColumnDirective>
                                    <ColumnDirective width={120}></ColumnDirective>
                                    <ColumnDirective width={120}></ColumnDirective>
                                    <ColumnDirective width={120}></ColumnDirective>
                                    <ColumnDirective width={120}></ColumnDirective>
                                    <ColumnDirective width={120}></ColumnDirective>
                                    <ColumnDirective width={100}></ColumnDirective>
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

### Limitation of Merge

The following features have some limitations in Merge:

* Merge with filter.
* Merge with wrap text.

## See Also

* [Rows and columns](./rows-and-columns)
* [Formatting](./formatting)
* [Hyperlink](./link)
* [Sorting](./sort)
* [Filtering](./filter)
