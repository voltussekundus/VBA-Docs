---
title: FileDialogFilters object (Office)
keywords: vbaof11.chm255000
f1_keywords:
- vbaof11.chm255000
ms.prod: office
api_name:
- Office.FileDialogFilters
ms.assetid: a74663cf-ad63-e41a-8d5e-e51e8a20c173
ms.date: 01/09/2019
ms.localizationpriority: medium
---


# FileDialogFilters object (Office)

A collection of **[FileDialogFilter](office.filedialogfilter.md)** objects that represent the types of files that can be selected in a file dialog box that is displayed by using the **FileDialog** object.

## Example

Use the **[Filters](office.filedialog.filters.md)** property of the **FileDialog** object to return a **FileDialogFilters** collection. The following code returns the **FileDialogFilters** collection for the **File Open** dialog box.

```vb
Application.FileDialog(msoFileDialogOpen).Filters
```

Use the **Add** method to add **FileDialogFilter** objects to the **FileDialogFilters** collection. 

The following example uses the **Clear** method to clear the collection and then adds filters to the collection. The **Clear** method completely empties the collection; however, if you don't add any filters to the collection after you clear it, the "All files (*.*)" filter is added automatically.

```vb
Sub Main() 
 
    'Declare a variable as a FileDialog object. 
    Dim fd As FileDialog 
 
    'Create a FileDialog object as a File Picker dialog box. 
    Set fd = Application.FileDialog(msoFileDialogFilePicker) 
 
    'Declare a variable to contain the path 
    'of each selected item. Even though the path is aString, 
    'the variable must be a Variant because For Each...Next 
    'routines only work with Variants and Objects. 
    Dim vrtSelectedItem As Variant 
 
    'Use a With...End With block to reference the FileDialog object. 
    With fd 
 
        'Change the contents of the Files of Type list. 
        'Empty the list by clearing the FileDialogFilters collection. 
        .Filters.Clear 
 
        'Add a filter that includes all files. 
        .Filters.Add "All files", "*.*" 
 
        'Add a filter that includes GIF and JPEG images and make it the first item in the list. 
        .Filters.Add "Images", "*.gif; *.jpg; *.jpeg", 1 
 
        'Use the Show method to display the File Picker dialog box and return the user's action. 
        'The user pressed the button. 
        If .Show = -1 Then 
 
            'Step through eachString in the FileDialogSelectedItems collection. 
            For Each vrtSelectedItem In .SelectedItems 
 
                'vrtSelectedItem is aString that contains the path of each selected item. 
                'Use any file I/O functions that you want to work with this path. 
                'This example displays the path in a message box. 
                MsgBox "Path name: " & vrtSelectedItem 
 
            Next vrtSelectedItem 
        'The user pressed Cancel. 
        Else 
        End If 
    End With 
 
    'Set the object variable to Nothing. 
    Set fd = Nothing 
 
End Sub
```

<br/>

When changing the **FileDialogFilters** collection, remember that each application can only create an instance of a single **FileDialog** object. This means that the **FileDialogFilters** collection resets to its default filters whenever you call the **FileDialog** method with a new dialog box type. The following example iterates through the default filters of the **SaveAs** dialog box and displays the description of each filter that includes a Microsoft Excel file.

```vb
Sub Main() 
 
    'Declare a variable as a FileDialogFilters collection. 
    Dim fdfs As FileDialogFilters 
 
    'Declare a variable as a FileDialogFilter object. 
    Dim fdf As FileDialogFilter 
 
    'Set the FileDialogFilters collection variable to 
    'the FileDialogFilters collection of the SaveAs dialog box. 
    Set fdfs = Application.FileDialog(msoFileDialogSaveAs).Filters 
 
    'Iterate through the description and extensions of each 
    'default filter in the SaveAs dialog box. 
    For Each fdf In fdfs 
 
        'Display the description of filters that include 
        'Microsoft Excel files 
        If InStr(1, fdf.Extensions, "xls", vbTextCompare) > 0 Then 
            MsgBox "Description of filter: " & fdf.Description 
        End If 
    Next fdf 
 
End Sub
```

> [!NOTE] 
> A run-time error occurs if the **Filters** property is used in conjunction with the **Clear**, **Add**, or **Delete** methods when applied to a Save As **FileDialog** object. For example, **Application.FileDialog([msoFileDialogSaveAs](office.msofiledialogtype.md)).Filters.Clear** will result in a run-time error.


## See also

- [FileDialogFilters object members](overview/library-reference/filedialogfilters-members-office.md)
- [Object Model Reference](overview/Library-Reference/reference-object-library-reference-for-office.md)

[!include[Support and feedback](~/includes/feedback-boilerplate.md)]