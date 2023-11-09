# Lay out multiple widgets vertically and horizontally

One of the most common layout patterns is to arrange widgets vertically or horizontally. 

You can use a Row widget to arrange widgets horizontally, and a Column widget to arrange widgets vertically.

**What's the point?**

Row and Column are two of the most commonly used layout patterns.

Row and Column each take a list of child widgets.

A child widget can itself be a Row, Column, or other complex widget.

You can specify how a Row or Column aligns its children, both vertically and horizontally.

You can stretch or constrain specific child widgets.

You can specify how child widgets use the Row’s or Column’s available space.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------

To create a row or column in Flutter, you add a list of children widgets to a Row or Column widget. In turn, each child can itself be a row or column, and so on. 

The following example shows how it is possible to nest rows or columns inside of rows or columns.

This layout is organized as a Row. The row contains two children: a column on the left, and an image on the right:

![image](https://github.com/luiscoco/flutter_layouts_VERY-IMPORTANT-EXAMPLE/assets/32194879/fea33b07-6480-4d7a-9cb2-8729e967bc26)

The left column’s widget tree nests rows and columns.

![image](https://github.com/luiscoco/flutter_layouts_VERY-IMPORTANT-EXAMPLE/assets/32194879/8466cb7c-47b4-4e77-8c68-9d98c1fed69f)
