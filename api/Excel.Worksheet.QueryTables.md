---
title: Worksheet.QueryTables property (Excel)
keywords: vbaxl10.chm175137
f1_keywords:
- vbaxl10.chm175137
ms.prod: excel
api_name:
- Excel.Worksheet.QueryTables
ms.assetid: 1228c6e0-f8d9-87a3-2fbf-1526f5229f1b
ms.date: 05/30/2019
ms.localizationpriority: medium
---


# Worksheet.QueryTables property (Excel)

Returns the **[QueryTables](Excel.QueryTables.md)** collection that represents all the query tables on the specified worksheet. Read-only.


## Syntax

_expression_.**QueryTables**

_expression_ A variable that represents a **[Worksheet](Excel.Worksheet.md)** object.


## Example

This example refreshes all query tables on worksheet one.

```vb
For Each qt in Worksheets(1).QueryTables 
 qt.Refresh 
Next
```

<br/>

This example sets query table one so that formulas to the right of it are automatically updated whenever it's refreshed.

```vb
Sheets("sheet1").QueryTables(1).FillAdjacentFormulas = True
```



[!include[Support and feedback](~/includes/feedback-boilerplate.md)]
