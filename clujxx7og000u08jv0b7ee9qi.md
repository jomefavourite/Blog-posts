---
title: "How to Center Image CSS for Beautiful Web Layouts"
seoTitle: "How to Center Image CSS for Beautiful Web Layouts"
seoDescription: "Learn CSS image centering techniques, including margin, flexbox, and grid, with examples. Perfect for developers"
datePublished: Wed Apr 03 2024 15:05:50 GMT+0000 (Coordinated Universal Time)
cuid: clujxx7og000u08jv0b7ee9qi
slug: how-to-center-image-css-for-beautiful-web-layouts
canonical: https://purecode.ai/blogs/center-image-css/
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1712156593514/92e592c1-83ea-4c47-808a-5a727a6bd7b9.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1712156612553/815c5a2c-811b-45f7-af18-1f95889ce05e.jpeg
tags: css

---

Ever spent hours wrestling with images that refuse to stay put in your web layouts? You're not alone.

In this comprehensive guide, we will unravel the mystery behind different image centering methods, from the basic and widely used to the more advanced and responsive techniques. Whether you're a seasoned web developer looking to refine your skills or a newcomer eager to understand the nuances of CSS, this article aims to demystify the process of image centering. From margin-based approaches to the flexbox and grid systems, we will navigate through a spectrum of techniques, ensuring that you not only comprehend the concepts but also gain practical insights through illustrative examples.

Let's demystify image centering and empower you to create visually stunning and well-balanced web pages with the precision that CSS provides. We’ll go over 5 methods that can be used to center images.

## Methods of Centering Images in CSS

We'll go over these 5 different methods of centering images be it vertically and horizontally, and also the limitations that come with each method.

* Using text-align Property.
    
* Using Margin Property.
    
* Using Flexbox Property.
    
* Using Grid Property.
    
* Using the Position Property.
    

https://youtu.be/mwVNVxpkly0?si=HbtzaD16ZdqzitZh

## **Method 1: Using text-align property to Center an Image**

The **text-align** property, although primarily designed for text alignment, can also be a quick and straightforward method to center images horizontally within their container. By applying **text-align: center** to the container, you leverage its alignment capabilities to achieve a centered image without complex CSS rules.

However, this method will only work when the image is wrapped in a block-level container such as a div element, and then on the parent component, the text-align property is used.

Here is a code snippet that shows how to use the text-align property:

```xml
<!-- HTML file -->
<body>
    <h1>Centering an Image with CSS</h1>
    <div class="container">
        <img src="https://buffer.com/library/content/images/size/w1200/2023/10/free-images.jpg" width="300">
    </div>
</body>
```

```xml
/* CSS file */
.container{
   text-align: center;
}

.container img {
   /* Additional styles for the image, if needed */
}
```

**Preview:**

![](https://purecode.ai/blogs/wp-content/uploads/2024/01/5d5d227d-2c26-4cc5-800d-aae89b9126ba.png align="left")

### Limitation using the text-align property

However, there are some limitations when using the **text-align** property for centering images:

* **Issue of container width**: If the container has a specified width and the image is wider than the container, it won't be centered. In such cases, you might need to ensure that the container is wide enough to accommodate the image.
    
* **Issue of Vertical Alignment:** The **text-align** property only handles horizontal alignment. If you need to vertically center the image, you might need additional techniques, such as using Flexbox or CSS Grid properties which will be discussed later on in this guide.
    

## Method 2: Using Margin property **to Center an Image**

The **margin** property can be used to center an image horizontally within it’s container (parent element). By setting the left and right margins to **auto** and using **text-align: center** as a complementary measure for older versions of Internet Explorer, this method provides a reliable way to achieve image centering.

Here is a code snippet that shows how to use the margin property:

```xml
<!-- HTML file -->
<div class="container">
  <img src="https://images.unsplash.com/photo-1660866838821-0c12213703df?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDEyfHx8ZW58MHx8fHx8&w=1000&q=80" width="500" alt="Centered Image">
</div>
```

```xml
/* CSS file */
.container {
  text-align: center; /* For older versions of IE */
}

.container img {
  display: block; /* Ensures block-level behavior for margins */
  margin-left: auto;
  margin-right: auto;
  /* Additional styles for the image, if needed */
}
```

**Preview:**

![](https://purecode.ai/blogs/wp-content/uploads/2024/01/2649b5a9-71dd-4428-a050-09c3440bfa58.png align="left")

**Explanation of the above code:**

* **text-align: center** is used on the container to ensure compatibility with older versions of Internet Explorer. It’s a good practice to add this property in the parent container, but the margin property is well-supported across major browsers now.
    
* **display: block** is applied to the image to make it a block-level element, allowing the use of auto margins.
    
* **margin-left: auto** and **margin-right: auto** set the left and right margins to auto, effectively centering the image horizontally.
    
* **image width** specified as 500px
    

### Limitation of using the margin property

* **Horizontal Centering Only:** The primary limitation of using **margin** for centering is that it only handles horizontal centering. If vertical centering is required, additional techniques or properties need to be employed.
    
* **Requires a Defined Width:** The margin: auto; trick relies on the image having a specific width set. Without a defined width, the browser won't have a clear reference for distributing the margins evenly. This can sometimes limit layout flexibility if you need the image to adjust its width dynamically.
    
* **Not Ideal for Responsive Design:** While **margin** can be effective for fixed-width layouts, it may not be the best choice for responsive designs. For responsive centering, techniques like Flexbox or CSS Grid are often preferred.
    

## Method 3: Using Flexbox property **to Center Images**

Flexbox provides a powerful and flexible layout model, making it an excellent choice for centering elements, including images, both horizontally and vertically. By applying the **display: flex;** property to the container and using alignment properties, you can achieve precise control over the positioning of your images.

https://youtu.be/K4N5HbituW4?si=Bupm2WmsD9qTebWb

Now, let’s see how to position images to the center using Flexbox both Horizontally and Vertically.

### Horizontal Centering with Flexbox

Here's how you can achieve horizontal centering using Flexbox:

```xml
<!-- HTML file -->
<div class="container">
  <img src="https://buffer.com/library/content/images/size/w1200/2023/10/free-images.jpg" width="500">
</div>
```

```xml
/* CSS file */
.container {
  display: flex;
  justify-content: center;
  /* Additional styles for the container, if needed */
}

.container img {
  /* Additional styles for the image, if needed */
}
```

**Preview:**

![](https://purecode.ai/blogs/wp-content/uploads/2024/01/fd9e1a90-79cd-49c8-b3f2-24a899ea7c54.png align="left")

> The border line around the image signifies the container width.

**Explanation:**

* **display: flex;** is applied to the container, turning it into a flex container.
    
* **justify-content: center;** horizontally centers the image within the container.
    
* Additional styles for the container and image can be adjusted based on design requirements.
    

---

Since the flexbox property stacks the flex items horizontally by default we could have multiple images in the container positioned horizontally and aligned in the center of the container. Below is an image illustrating this, notice the green border line which signifies the container width.

![](https://purecode.ai/blogs/wp-content/uploads/2024/01/53a60ac9-83fc-4b39-836e-2965e2177256.png align="left")

To achieve the preview above, here's the code snippet

```xml
<!-- HTML file -->
<div class="container">
    <img src="https://buffer.com/library/content/images/size/w1200/2023/10/free-images.jpg" width="300">
    <img src="https://images.unsplash.com/photo-1660866838821-0c12213703df?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDEyfHx8ZW58MHx8fHx8&w=1000&q=80" width="300">
</div>
```

```xml
/* CSS file */
.container {
      display: flex;
      justify-content: center;
}
```

### Vertical Centering with Flexbox

To illustrate the vertical centering of images, the flexbox container needs to have a height greater than the image height. Here's how you can achieve vertical centering of an image using Flexbox:

```xml
<!-- HTML file -->
<div class="container">
  <img src="https://buffer.com/library/content/images/size/w1200/2023/10/free-images.jpg" width="500">
</div>
```

```xml
/* CSS file */
.container {
  display: flex;
  align-items: center;
  height: 80vh;
  /* Additional styles for the container, if needed */
}

.container img {
  /* Additional styles for the image, if needed */
}
```

**Preview:**

![](https://purecode.ai/blogs/wp-content/uploads/2024/01/5ea9ad10-c0d5-4d4f-9bea-e0e4f13bf947.png align="left")

**Explanation:**

The **align-items: center** property is used here to position the image vertically to the center of the flex container.

* **align-items: center;** vertically centers the image within the container.
    
* **height;** this property is needed so that the image would be positioned vertically, in the example above 80vh was used but it could be any length value as far as it's greater than the height of the image.
    

Add more images to the flex container while still using the align-items center property, would look like this.

![](https://purecode.ai/blogs/wp-content/uploads/2024/01/2e2c2ad4-0ab6-4a83-9af8-3040e68c7106.png align="left")

### Centering Images both Horizontally and Vertically

In the case where there are multiple images and you'd like to center the images vertically and horizontally, here's how to do so:

![](https://purecode.ai/blogs/wp-content/uploads/2024/01/d5cd430a-7b3f-4137-bd6c-f8ab333695bb.png align="left")

```xml
<!-- HTML file -->
<div class="container">
    <img src="https://buffer.com/library/content/images/size/w1200/2023/10/free-images.jpg" width="300">
    <img src="https://images.unsplash.com/photo-1660866838821-0c12213703df?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDEyfHx8ZW58MHx8fHx8&w=1000&q=80" width="300">
</div>
```

```xml
/* CSS file */ 
.container {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 80vh;
  }
```

**Explaination**

* The **justify content** property with the value **center** positions the images (or flex items) on the [main axis](https://developer.mozilla.org/en-US/docs/Glossary/Main_Axis), that is horizontally, while
    
* The **align-items** property with **center** as its value positions the images vertically on the [cross-axis](https://developer.mozilla.org/en-US/docs/Glossary/Cross_Axis)
    

### **Advantages of using Flexbox to center images:**

1. **Simple and Intuitive Syntax:** Flexbox offers a relatively straightforward way to align and distribute elements within a container, making it easier to achieve image centering compared to traditional methods like floats and positioning.
    
2. **Horizontal and Vertical Centering:** With Flexbox, you can center images both horizontally and vertically within their container using just a few properties. This eliminates the need for workarounds or extra markup.
    
3. **Responsiveness:** Flexbox layouts are inherently responsive, adapting seamlessly to different screen sizes and device orientations. Your centered images will maintain their alignment across various viewports.
    
4. **Flexibility for Additional Elements:** Flexbox can handle multiple elements within a container, allowing you to center images alongside text or other content while maintaining a consistent layout.
    
5. **Control over Distribution and Alignment:** Flexbox provides granular control over the distribution and alignment of items within a flex container. You can fine-tune the spacing and arrangement of images as needed.
    

### **Limitations of using Flexbox to center images:**

1. **Potential Nesting Complexity:** When working with complex layouts, nesting Flexbox containers can sometimes lead to unexpected results or make the code harder to maintain. Careful planning is crucial.
    
2. **Not Ideal for All Scenarios:** Flexbox is not a silver bullet for all layout challenges. For complex image galleries or intricate arrangements, other layout techniques like grid or CSS tables may be more suitable.
    

> To learn more about using the flexbox properties, please visit the [Flexbox MDN documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_flexible_box_layout/Basic_concepts_of_flexbox)

Since we're covering centering images in CSS, why don't you check out [PureCode.ai](https://purecode.ai/); we’ve got over 1000+ AI-generated UI components, which will enable you to skip the tedious work of creating components yourself. Check [PureCode](https://purecode.ai/) out today.

![](https://purecode.ai/blogs/wp-content/uploads/2024/01/f85058bf-5b98-48bf-a4d8-6900cd3a896d.png align="left")

## Method 4: Using Grid property **to Center Images**

CSS Grid provides a powerful two-dimensional layout system, making it a versatile choice for centering elements within a container.

### Horizontal Centering with Grid

Using the Grid property there are various ways to horizontally center an image or images because of the two-dimensional layout system CSS grid provides, but we'll be going over one method since the other process are similar.

#### **Using justify-items: center**

This approach centers all items, in this case, the image element within the grid container horizontally on their designated lines. Below is an example illustrating how to achieving this:

```xml
<!-- HTML file -->
<div class="container">
  <img src="https://images.unsplash.com/photo-1660866838821-0c12213703df?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDEyfHx8ZW58MHx8fHx8&w=1000&q=80" width="100%">
</div>
```

```xml
/* CSS file */
.container {
  display: grid;
  justify-items: center;
  /* Additional styles for the container, if needed */
}

.container img {
  /* Additional styles for the image, if needed */
}
```

**Preview**

![](https://purecode.ai/blogs/wp-content/uploads/2024/01/2e7c54f1-5e48-4cee-8c4b-1bc013defba9.png align="left")

**Explaination**

* The **display** property as **grid** makes the container selector become a grid container.
    
* The **justify-items** property with the value **center** positions the images (or grid items) on the inline axis, that is horizontally
    

#### Horizontal Centering of **Multiple Images with Grid**

To horizontally align multiple images with the grid property, we'll need to specify the [grid tracks](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_grid_layout/Basic_concepts_of_grid_layout#grid_tracks) using the [grid-template-colomns](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-columns) property.

![](https://purecode.ai/blogs/wp-content/uploads/2024/01/93019b7f-8952-4402-9957-ec742b8302a6.png align="left")

Example code:

```xml
<!-- HTML file -->
 <div class="container">
    <img src="https://buffer.com/library/content/images/size/w1200/2023/10/free-images.jpg" width="300">
  
    <img src="https://images.unsplash.com/photo-1660866838821-0c12213703df?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDEyfHx8ZW58MHx8fHx8&w=1000&q=80" width="300">
  </div>
```

```xml
/* CSS file */
.container {
      display: grid;
      grid-template-columns: repeat(2, 1fr); 
      justify-items: center;
}
    
.container img {
      /* Additional styles for the image, if needed */
 }
```

**Explaination:**

* The **display: grid** property and value makes the container selector a grid container
    
* **grid-template-columns: repeat(2, 1fr);** defines the size of the column tracks. In this case, we'll have 1fr unit for 2 columns, where the 2 images would reside.
    
* **justify-items: center;** positions the images horizontally center within the columns.
    

### Vertical Centering with Grid

Here are an approach to achieve vertical centering with Grid:

**Using align-items: center;**

```xml
<!-- HTML file -->
 <div class="container">
    <img src="https://buffer.com/library/content/images/size/w1200/2023/10/free-images.jpg" width="300">
  </div>
```

```xml
/* CSS file */
.container {
      display: grid;
      align-items: center;
      height: 80vh;
}
    
.container img {
      /* Additional styles for the image, if needed */
 }
```

**Preview:**

![](https://purecode.ai/blogs/wp-content/uploads/2024/01/ed19127c-20e0-4c81-b370-62e898daa49b.png align="left")

**Explanation:**

* The **display: grid** property and value makes the container selector a grid container
    
* The **align-items** property **center** as its value positions the images vertically on the [block axis](https://developer.mozilla.org/en-US/docs/Web/CSS/align-items)
    
* **height: 80vh;** is used to show how the image is center vertically.
    

For multiple images, specifing the **grid-template-columns** property would do the trick.

![](https://purecode.ai/blogs/wp-content/uploads/2024/01/640c3225-0b94-48f3-a44c-983cb4867821.png align="left")

### Centering Images both Horizontally and Vertically

Using the place-items: center; oroperties which is an [shorthand property](https://developer.mozilla.org/en-US/docs/Web/CSS/Shorthand_properties) for the [align-items](https://developer.mozilla.org/en-US/docs/Web/CSS/align-items) and [justify-items](https://developer.mozilla.org/en-US/docs/Web/CSS/justify-items) properties, would center images both horizontally and vertically.

```xml
<!-- HTML file -->
<div class="container">
  <img src="https://buffer.com/library/content/images/size/w1200/2023/10/free-images.jpg" alt="Centered Image">

<img src="https://images.unsplash.com/photo-1660866838821-0c12213703df?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDEyfHx8ZW58MHx8fHx8&w=1000&q=80" width="300">
</div>
```

```xml
/* CSS file */
.container {
  display: grid;
  place-items: center;
  /* Additional styles for the container, if needed */
}

.container img {
  /* Additional styles for the image, if needed */
}
```

**Preview:**

![](https://purecode.ai/blogs/wp-content/uploads/2024/01/2d603fb7-e2ae-4358-a48d-a55436e8783b.png align="left")

**Explanation:**

* **display: grid;** is applied to the container, establishing it as a grid container.
    
* **place-items: center;** is a shorthand property for both **align-items: center;** and **justify-items: center;** effectively centering the content within the grid.
    
* Additional styles for the container and image can be adjusted based on design requirements.
    

### **Advantages of Using Grid:**

* **Powerful Layout Control:** Grid provides flexible and precise control over the placement of elements within a container.
    
* **Multidimensional Layouts:** Grid can handle complex layouts with multiple rows and columns, making it suitable for image galleries or other intricate arrangements.
    

### **Limitations of Using Grid:**

* **Browser Compatibility:** While modern browsers have excellent support for Grid, older browsers may require fallbacks or polyfills.
    
* **Learning Curve:** Grid syntax can be more complex to learn compared to Flexbox, especially for those new to CSS layout techniques.
    

## Method 5: Using the Position property **to Center Images**

The **position property**, along with **top, right, bottom, and left,** can be employed to center an image within its container. While not as flexible as some layout models like Flexbox or Grid, this method provides an alternative for centering when other techniques may not be suitable.

Here's how to achieve centering an image with the position property:

```xml
<div class="container">
  <img src="https://images.unsplash.com/photo-1660866838821-0c12213703df?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDEyfHx8ZW58MHx8fHx8&w=1000&q=80" alt="Centered Image" width="300">
</div>
```

```xml
/* CSS file */ 
.container img {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      /* Additional styles for the image, if needed */
  }
```

**Preview:**

![](https://purecode.ai/blogs/wp-content/uploads/2024/01/026507b1-c2a1-4603-9318-3aa9dfdaeecf.png align="left")

**Explanation:**

* **position: relative;** is applied to the container to establish a positioning context for the absolute positioning of the image.
    
* **position: absolute;** removes the image from the normal document flow, allowing precise positioning within its nearest positioned ancestor.
    
* **top: 50%;** and **left: 50%;** position the image's top-left corner at the center of the container.
    
* **transform: translate(-50%, -50%);** centers the image perfectly by adjusting it based on its own dimensions.
    

### **Advantages:**

* **Absolute Precision:** This method allows for precise control over the positioning of the image, making it suitable for unique layout requirements.
    
* **Cross-Browser Compatibility:** The approach is widely supported across browsers, including older versions.
    

### Limitation using the Position property

* **Static Container Size:** The container's size needs to be known in advance for accurate centering.
    
* **Not as Flexible:** Compared to Flexbox or Grid, this method may require adjustments for responsive designs or dynamic content.
    
* **Potential Overlapping:** Be cautious when using absolute positioning to avoid overlapping with other elements.
    

## Difference between all 5 methods

<table><tbody><tr><td colspan="1" rowspan="1"><p><strong>Method</strong></p></td><td colspan="1" rowspan="1"><p><strong>Description</strong></p></td><td colspan="1" rowspan="1"><p><strong>Advantages</strong></p></td><td colspan="1" rowspan="1"><p><strong>Limitations</strong></p></td></tr><tr><td colspan="1" rowspan="1"><p><strong>Using text-align Property</strong></p></td><td colspan="1" rowspan="1"><p>Centrally aligns an image horizontally within its container using <code>text-align: center;</code>.</p></td><td colspan="1" rowspan="1"><p>- Quick and simple implementation.<br>- Suitable for basic layouts.</p></td><td colspan="1" rowspan="1"><p>- Limited to horizontal centering.</p></td></tr><tr><td colspan="1" rowspan="1"><p><strong>Using Margin Property</strong></p></td><td colspan="1" rowspan="1"><p>Uses <code>margin: auto;</code> to center an image both horizontally and vertically within its container.</p></td><td colspan="1" rowspan="1"><p>- Simple and widely supported.<br>- Supports both horizontal and vertical centering.</p></td><td colspan="1" rowspan="1"><p>- Requires the image to be a block-level element.<br>- Not as flexible for complex layouts.</p></td></tr><tr><td colspan="1" rowspan="1"><p><strong>Using Flexbox Property</strong></p></td><td colspan="1" rowspan="1"><p>Utilizes <code>display: flex;</code> with <code>justify-content: center;</code> and <code>align-items: center;</code> for versatile horizontal and vertical centering.</p></td><td colspan="1" rowspan="1"><p>- Versatile for both horizontal and vertical centering.<br>- Great for responsive design.</p></td><td colspan="1" rowspan="1"><p>- Single-axis limitation.<br>- Default behavior of flex items may require additional adjustments.</p></td></tr><tr><td colspan="1" rowspan="1"><p><strong>Using Grid Property</strong></p></td><td colspan="1" rowspan="1"><p>Applies <code>display: grid;</code> to create a two-dimensional layout, providing comprehensive control over image centering.</p></td><td colspan="1" rowspan="1"><p>- Excellent for complex layouts.<br>- Precise control over alignment.</p></td><td colspan="1" rowspan="1"><p>- Learning curve for advanced features.<br>- May require vendor prefixes for older browser compatibility.</p></td></tr><tr><td colspan="1" rowspan="1"><p><strong>Using Position Property</strong></p></td><td colspan="1" rowspan="1"><p>Utilizes <code>position: absolute;</code> with <code>top: 50%;</code>, <code>left: 50%;</code>, and <code>transform: translate(-50%, -50%);</code> for precise centering of an image relative to its container.</p></td><td colspan="1" rowspan="1"><p>- Absolute precision in centering.<br>- Suitable for unique layout requirements.</p></td><td colspan="1" rowspan="1"><p>- Requires knowledge of container dimensions.<br>- May not be as flexible for responsive designs.</p></td></tr></tbody></table>

## Frequently Asked Questions

### How do I center images in CSS?

You can center images using any of these methods

* **Flexbox** is often preferred for its simplicity and responsiveness.
    
* **Grid** is powerful for complex layouts and multiple images.
    
* **Text-align** is quick for basic horizontal centering.
    
* **Auto margins** are useful for images with known widths.
    
* **Position property** offers precise control but requires more understanding.
    

### How do I center an absolute image in a div?

* Using the **Position and Transform** if you need precise control over the image's absolute positioning within the div.
    
* Consider **Flexbox or Grid** when you want simplicity and responsiveness, especially if centering other elements alongside the image.
    

## **Final thoughts on Centering Images with CSS**

Congratulations on completing this journey through various CSS techniques for image centering! By now, you've gained insights into different methods each offering its unique advantages. Demystifying image centering with CSS opens up a world of possibilities for creating visually appealing and well-structured web designs. Whether you're a beginner or an experienced developer, mastering these techniques empowers you to tackle diverse design challenges with confidence.

Check out [Purecode.ai](https://purecode.ai/) today, for streamlining front-end code creation.