---
header_type: hero
header_img: https://picsum.photos/id/1018/2000/2000
title: Shopify custom FAQ page
subtitle: How to use Shopify Metaobjects to build a custom FAQ page for your Shopify store
tags:
  - shopify
  - metaobjects
categories: []
show_sociallinks: false
layout: post
---


In this post I will walk you through how you can use Shopify Metaobjects to create a custom FAQ page in your Shopify store.

The custom FAQ page I created uses dynamic CSS, liquid and metaobjects to create a fully customizable page that allows the Shopify admin to exclude or include sections and items by country. We originally decided to build this new FAQ page since the existing FAQ page included an iFrame that linked out to an FAQ page from a Shopify app and while it worked it didn't meet all of our needs. The frame took quite a bit of time to load when the user hit the page and wasn’t able to be styled using css so it didn’t fit in with the rest of the site. 

The one aspect of the previous FAQ was that we did like is that it leveraged an accordion view where each item was collapsed until the user expanded it. We wanted to maintain this look and functionality but also wanted to be able to style it so that it matched the rest of the site.

Another reason for implementing a new FAQ page was because we modified our theme to be able to produce a different experience based on the shopper’s target region. When the user selects Germany as their region they get more of a "catalog" experience and are directed to an external distributor to purchase their item. As a result there were many of the FAQ items and in fact a whole section that we didn’t want displayed when this region was chosen. This new FAQ page allows the Shopify admin to exclude certain sections and individual items from being displayed.

Here are the steps to follow:

Step 1 (New page template)
* Create new page in the theme customizer (this will create a new template we can use)

Step 2 (New page on site)
* Add new site page using this new theme as the theme template

Step 3 (New Section)
*	Create a new section that will be consumed by the new template
*	Copy the contents of main-page to this new section
*	Modify the code of the new page created in Step 1 to consume the new section
*	Tweak some of the code as needed
*	Remove the page.content tag and add {% raw %}{% render ‘FAQ’ %}{% endraw %}

Step 4 (FAQ snippet)
*	Add in a snippet named ‘FAQ’
*	Add in code to FAQ snippet

Step 5 (New css file)
*	Create a new asset named faqstyles.css.liquid
*	Paste in the sample css.liquid code
*	You may need to adjust the css styling to best fit your existing theme

Step 6 (Setup Metaobjects)
*	Setup metaobject definitions
*	Add in category and item entries

<!---
{ include snippets/video.html id="QC6X82l0-1c" provider="youtube" nolazy="true"}
--->


