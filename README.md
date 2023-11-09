# Lay out multiple widgets vertically and horizontally

One of the most common layout patterns is to arrange widgets vertically or horizontally. 

You can use a Row widget to arrange widgets horizontally, and a Column widget to arrange widgets vertically.

**What's the point?**

**Row** and **Column** are two of the most commonly used layout patterns.

**Row** and **Column** each take a list of child widgets.

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

## Sizing widgets

When a layout is too large to fit a device, a yellow and black striped pattern appears along the affected edge. 

Here is an example of a row that is too wide:

![image](https://github.com/luiscoco/flutter_layouts_VERY-IMPORTANT-EXAMPLE/assets/32194879/a6644230-4aa0-42a1-ad56-edf41e0e02f6)

Widgets can be sized to fit within a row or column by using the Expanded widget. 

To fix the previous example where the row of images is too wide for its render box, wrap each image with an Expanded widget.

```dart
Row(
  crossAxisAlignment: CrossAxisAlignment.center,
  children: [
    Expanded(
      child: Image.asset('images/pic1.jpg'),
    ),
    Expanded(
      child: Image.asset('images/pic2.jpg'),
    ),
    Expanded(
      child: Image.asset('images/pic3.jpg'),
    ),
  ],
);
```

![image](https://github.com/luiscoco/flutter_layouts_VERY-IMPORTANT-EXAMPLE/assets/32194879/91355376-1bcb-4bfa-adfe-7166bba7ec01)

https://api.flutter.dev/flutter/widgets/Expanded-class.html

**App source code:** https://github.com/flutter/website/tree/main/examples/layout/sizing

Perhaps you want a widget to occupy twice as much space as its siblings. 

For this, use the Expanded widget flex property, an integer that determines the flex factor for a widget. 

The default flex factor is 1. The following code sets the flex factor of the middle image to 2:

```dart
Row(
  crossAxisAlignment: CrossAxisAlignment.center,
  children: [
    Expanded(
      child: Image.asset('images/pic1.jpg'),
    ),
    Expanded(
      flex: 2,
      child: Image.asset('images/pic2.jpg'),
    ),
    Expanded(
      child: Image.asset('images/pic3.jpg'),
    ),
  ],
);
```

![image](https://github.com/luiscoco/flutter_layouts_VERY-IMPORTANT-EXAMPLE/assets/32194879/da403b7d-481c-48dc-b720-26d7a417fcbf)

## Packing widgets

By default, a row or column occupies as much space along its main axis as possible, but if you want to pack the children closely together, set its mainAxisSize to MainAxisSize.min. 

The following example uses this property to pack the star icons together.

```dart
Row(
  mainAxisSize: MainAxisSize.min,
  children: [
    Icon(Icons.star, color: Colors.green[500]),
    Icon(Icons.star, color: Colors.green[500]),
    Icon(Icons.star, color: Colors.green[500]),
    const Icon(Icons.star, color: Colors.black),
    const Icon(Icons.star, color: Colors.black),
  ],
)
```

![image](https://github.com/luiscoco/flutter_layouts_VERY-IMPORTANT-EXAMPLE/assets/32194879/cc4dc014-44b2-48cc-8d0d-6aae9dc10c1c)

**App source code:** https://github.com/flutter/website/tree/main/examples/layout/pavlova

## Nesting rows and columns

The layout framework allows you to nest rows and columns inside of rows and columns as deeply as you need.

Let’s look at the code for the outlined section of the following layout:

![image](https://github.com/luiscoco/flutter_layouts_VERY-IMPORTANT-EXAMPLE/assets/32194879/2a0063bb-647a-4c44-b3df-64b305f024b6)

The outlined section is implemented as two rows. The **ratings row** contains five stars and the number of reviews. The icons row contains three columns of icons and text.

The widget tree for the **ratings row**:

![image](https://github.com/luiscoco/flutter_layouts_VERY-IMPORTANT-EXAMPLE/assets/32194879/9f2a6250-4579-4f7f-9983-ad9f5cb2e192)

The ratings variable creates a row containing a smaller row of 5 star icons, and text:

```dart
var stars = Row(
  mainAxisSize: MainAxisSize.min,
  children: [
    Icon(Icons.star, color: Colors.green[500]),
    Icon(Icons.star, color: Colors.green[500]),
    Icon(Icons.star, color: Colors.green[500]),
    const Icon(Icons.star, color: Colors.black),
    const Icon(Icons.star, color: Colors.black),
  ],
);

final ratings = Container(
  padding: const EdgeInsets.all(20),
  child: Row(
    mainAxisAlignment: MainAxisAlignment.spaceEvenly,
    children: [
      stars,
      const Text(
        '170 Reviews',
        style: TextStyle(
          color: Colors.black,
          fontWeight: FontWeight.w800,
          fontFamily: 'Roboto',
          letterSpacing: 0.5,
          fontSize: 20,
        ),
      ),
    ],
  ),
);
```

To minimize the visual confusion that can result from heavily nested layout code, implement pieces of the UI in variables and functions.

The **icons row**, below the ratings row, contains 3 columns; each column contains an icon and two lines of text, as you can see in its widget tree:

![image](https://github.com/luiscoco/flutter_layouts_VERY-IMPORTANT-EXAMPLE/assets/32194879/09fb86d3-1a11-4c7a-a23e-5989e5911686)

The iconList variable defines the icons row:

```dart
const descTextStyle = TextStyle(
  color: Colors.black,
  fontWeight: FontWeight.w800,
  fontFamily: 'Roboto',
  letterSpacing: 0.5,
  fontSize: 18,
  height: 2,
);

// DefaultTextStyle.merge() allows you to create a default text
// style that is inherited by its child and all subsequent children.
final iconList = DefaultTextStyle.merge(
  style: descTextStyle,
  child: Container(
    padding: const EdgeInsets.all(20),
    child: Row(
      mainAxisAlignment: MainAxisAlignment.spaceEvenly,
      children: [
        Column(
          children: [
            Icon(Icons.kitchen, color: Colors.green[500]),
            const Text('PREP:'),
            const Text('25 min'),
          ],
        ),
        Column(
          children: [
            Icon(Icons.timer, color: Colors.green[500]),
            const Text('COOK:'),
            const Text('1 hr'),
          ],
        ),
        Column(
          children: [
            Icon(Icons.restaurant, color: Colors.green[500]),
            const Text('FEEDS:'),
            const Text('4-6'),
          ],
        ),
      ],
    ),
  ),
);
```

