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

--------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Note:** **Row** and **Column** are basic primitive widgets for horizontal and vertical layouts—these low-level widgets allow for maximum customization.

Flutter also offers specialized, higher level widgets that might be sufficient for your needs. 

For example, instead of Row you might prefer **ListTile**, an easy-to-use widget with properties for leading and trailing icons, and up to 3 lines of text. 

Instead of Column, you might prefer **ListView**, a column-like layout that automatically scrolls if its content is too long to fit the available space. For more information, see Common layout widgets.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Aligning widgets

You control how a row or column aligns its children using the mainAxisAlignment and crossAxisAlignment properties. 

For a row, the main axis runs horizontally and the cross axis runs vertically. For a column, the main axis runs vertically and the cross axis runs horizontally.

![image](https://github.com/luiscoco/flutter_layouts_VERY-IMPORTANT-EXAMPLE/assets/32194879/00e6b33a-4c14-403d-8946-de77f76ec433)

The **MainAxisAlignment** and **CrossAxisAlignment** enums offer a variety of constants for controlling alignment.

**Note:** When you add images to your project, you need to update the pubspec.yaml file to access them—this example uses Image.asset to display the images. 

For more information, see this example’s pubspec.yaml file or Adding assets and images. You don’t need to do this if you’re referencing online images using Image.network.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Row sample

In the following example, each of the 3 images is 100 pixels wide. The render box (in this case, the entire screen) is more than 300 pixels wide, so setting the main axis alignment to spaceEvenly divides the free horizontal space evenly between, before, and after each image.

```dart
Row(
  mainAxisAlignment: MainAxisAlignment.spaceEvenly,
  children: [
    Image.asset('images/pic1.jpg'),
    Image.asset('images/pic2.jpg'),
    Image.asset('images/pic3.jpg'),
  ],
);
```

![image](https://github.com/luiscoco/flutter_layouts_VERY-IMPORTANT-EXAMPLE/assets/32194879/f08fa708-57e7-45e5-86bd-bde70650818d)

**App source code:** https://github.com/flutter/website/tree/main/examples/layout/row_column

### Column sample

**Columns** work the same way as rows. The following example shows a column of 3 images, each is 100 pixels high. The height of the render box (in this case, the entire screen) is more than 300 pixels, so setting the main axis alignment to spaceEvenly divides the free vertical space evenly between, above, and below each image.

```dart
Column(
  mainAxisAlignment: MainAxisAlignment.spaceEvenly,
  children: [
    Image.asset('images/pic1.jpg'),
    Image.asset('images/pic2.jpg'),
    Image.asset('images/pic3.jpg'),
  ],
);
```

![image](https://github.com/luiscoco/flutter_layouts_VERY-IMPORTANT-EXAMPLE/assets/32194879/0f1357e2-2097-4015-a49b-a2ed683e64d5)

**App source code:** https://github.com/flutter/website/tree/main/examples/layout/row_column




