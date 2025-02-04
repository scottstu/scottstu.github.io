---
header_type: hero
header_img: https://picsum.photos/id/626/2000/2000
title: Display availability ETA by product variant
subtitle: Use Shopify Metaobjects to add availability ETA for variants of a product that are out of stock
tags:
  - shopify
  - metaobjects
categories: []
show_sociallinks: true
show_tags: false
show_related: false
show_bottomnavs: false
layout: post
---

One of the things we wanted to be able to do in our store was to give our customer's more information about when a product is going to be available for sale and we needed to be able to control this at the product variant level.

Let's take a look at what this looks like in a demo store based on Dawn 15.2.0 before making any changes.

![Sold Out - Before view](/assets/img/site/inventory-ETA-Before-1.png){:style="display:block; margin-left:10px; border: 2px solid #999999; padding: 5px; width: 60%;"}

As you can see above the Dawn theme has a built function which displays "Sold out" if the item is not available. This function does not tell the end customer when the product will be available for sale again so we wanted to be able to show an estimated ETA at the product variant level. 

In order to get started we first need to add a metafield to our product variant objects and populate this with an ETA date for any items that are out of stock. In our production store we set the value of all variants to "Sold Out" and then configure dates on specific products we have an ETA for. If there is no known ETA we would just leave it as "Sold Out".

![Variant Sold Metafield Configuration](/assets/img/site/inventory-ETA-Variant-SoldOut-Metafield-Configuration.png){:style="display:block; margin-left:10px; border: 2px solid #999999; padding: 5px"}

The next step is that we need to modify the theme code to read in this value by variant and display it on the product card when the product is out of stock. This will vary by theme but we will show how this would work in the Dawn Theme in our demo store. In order to make changes to this we must change the data that is displayed when the user navigates directly to the page as well as the data that is displayed when they click on different variants within the product card. We needed to make changes to snippets/price.liquid, snippets/buy-buttons.liquid, snippets/product-variant-picker.liquid, and assets/product-info.js.

Once all the changes have been made you can now see that when the user selects the New Zealand model of this product they now see "SOLD OUT - ETA FEB 15" on both the product card as well as on the **Add to cart** button.

![Sold Out - After view](/assets/img/site/inventory-ETA-After-1.png){:style="display:block; margin-left:10px; border: 2px solid #999999; padding: 5px; width: 60%;"}

There are certainly other ways that this could have been accomplished through custom code or through an app however we felt it was the most flexible to be able to add this feature into our existing theme. We already have a number of customizations to our theme and this was an important one that we were able to build.

{% include contact-me.html %}