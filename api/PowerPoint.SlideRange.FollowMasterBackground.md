---
title: SlideRange.FollowMasterBackground property (PowerPoint)
keywords: vbapp10.chm532021
f1_keywords:
- vbapp10.chm532021
ms.prod: powerpoint
api_name:
- PowerPoint.SlideRange.FollowMasterBackground
ms.assetid: 0c409371-8ecc-ecf9-3d16-cbbd0009d825
ms.date: 06/08/2017
ms.localizationpriority: medium
---


# SlideRange.FollowMasterBackground property (PowerPoint)

Determines whether the range of slides follows the slide master background. Read/write.


## Syntax

_expression_. `FollowMasterBackground`

_expression_ A variable that represents a [SlideRange](PowerPoint.SlideRange.md) object.


## Return value

MsoTriState


## Remarks

The value of the **FollowMasterBackground** property can be one of these **MsoTriState** constants.



|Constant|Description|
|:-----|:-----|
|**msoFalse**|The specified slide or range of slides has a custom background.|
|**msoTrue**| The specified slide or range of slides follows the slide master background.|

When you create a new slide, the default value for this property is **True**. If you copy a slide from another presentation, it retains the setting it had in the original presentation. That is, if the slide followed the slide master background in the original presentation, it will automatically follow the slide master background in the new presentation; or, if the slide had a custom background, it will retain that custom background.

Note that the look of the slide's background is determined by the color scheme and background objects and by the background itself. If setting the **FollowMasterBackground** property alone doesn't give you the results you want, try setting the **ColorScheme** and **DisplayMasterShapes** properties as well.


## Example

This example copies slide one from presentation two, pastes the slide at the end of presentation one, and matches the slide's background, color scheme, and background objects to the rest of presentation one.


```vb
Presentations(2).Slides(1).Copy

With Presentations(1).Slides.Paste

    .FollowMasterBackground = msoTrue

    .ColorScheme = Presentations(1).SlideMaster.ColorScheme

    .DisplayMasterShapes = True

End With
```


## See also


[SlideRange Object](PowerPoint.SlideRange.md)

[!include[Support and feedback](~/includes/feedback-boilerplate.md)]