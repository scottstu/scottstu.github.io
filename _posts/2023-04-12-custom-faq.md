---
header_type: hero
header_img: https://picsum.photos/id/404/2000/2000
title: Shopify custom FAQ page
subtitle: How to use Shopify Metaobjects to build a custom FAQ page for your Shopify store
tags:
  - shopify
  - metaobjects
categories: []
show_sociallinks: false
show_tags: false
show_related: false
show_bottomnavs: false
layout: post
---


In this post I will walk you through how you can use Shopify Metaobjects to create a custom FAQ page in your Shopify store.

The custom FAQ page I created uses dynamic CSS, liquid and metaobjects to create a fully customizable page that allows the Shopify admin to exclude or include sections and items by country. We originally decided to build this new FAQ page since the existing FAQ page included an iFrame that linked out to an FAQ page from a Shopify app and while it worked it didn't meet all of our needs. The frame took quite a bit of time to load when the user hit the page and wasn’t able to be styled using css so it didn’t fit in with the rest of the site. 

The one aspect of the previous FAQ was that we did like is that it leveraged an accordion view where each item was collapsed until the user expanded it. We wanted to maintain this look and functionality but also wanted to be able to style it so that it matched the rest of the site.

Another reason for implementing a new FAQ page was because we modified our theme to be able to produce a different experience based on the shopper’s target region. When the user selects Germany as their region they get more of a "catalog" experience and are directed to an external distributor to purchase their item. As a result there were many of the FAQ items and in fact a whole category of items that we didn’t want displayed when this region was chosen. This new FAQ page allows the Shopify admin to exclude certain sections and individual items from being displayed.

The following table outlines the new files and components that were created as part of this solution.

| File / Component  | Type | Purpose
| ------------- | ------------- | ------------- |
| `page.faq.json` | Template | Base template that allows us to call the section that produces the FAQ page
| `faq-page.liquid` | Section  | Base section that displays the page title and renders the FAQ snippet
| `faq.liquid` | Snippet  | Snippet that reads the faq configuration from the metaobjects that were created and renders the html output
| `faqstyles.css.liquid` | Asset  | Dynamic CSS page that is used to style the FAQ page. It reads in 4 variables from the theme settings and applies them to the CSS that is rendered to the client
| FAQ Category | Metaobject  | Metaobject that stores the FAQ categories. They are referenced by the FAQ items.
| FAQ Item| Metaobject  | Metaobject that stores the FAQ items. They reference the FAQ categories



Here are the steps you can follow to build this yourself:

Step 1 - Create new page template `page.faq.json`
* Open the them customizer from your Shopify admin page and create a new template
* This new page will be based on the *Default page*
* This will create a new template we can use for our FAQ page

Step 2 - Create new page on site
* Add new site page using this new template as the theme template

Step 3 - Create new Section `faq-page.liquid`
*	Using the code editor create a new section that will be consumed by the new template
*	Copy the contents of `main-page.liquid` to this new section
*	Modify the code of `page.faq.json` created in Step 1 to consume the new section
    * under main/type change main-page to faq-page
*	Tweak some of the code in this section as needed
    * rename the section name to sections.faq-page.name
    * Remove the page.content tag and add {% raw %}{% render ‘FAQ’ %}{% endraw %}

Step 4 - Create new FAQ snippet
*	Using the code editor create a new snippet named `faq.liquid`
*	Copy in the sample code to the FAQ snippet

Step 5 - Create new `faqstyles.css.liquid`
*	Using the code editor create a new asset named faqstyles.css.liquid
*	Copy in the sample faqstyles.css.liquid code
*	You may need to adjust the css styling to best fit your existing theme

Step 6 - Create required Metaobjects
*	Setup metaobject definitions
*	Add in FAQ Category and FAQ Item entries

Here is a look at the final product.

![FAQ Final Product](/assets/img/site/FAQFinal.png){:style="display:block; margin-left:10px; border: 2px solid #999999; padding: 5px"}

Please check out my video where I walk through how to build this in Shopify.

{% include snippets/video.html id="zbUHRyxii5Y" provider="youtube" nolazy="true" %}

<br>
All of the files used in this video can be found here:
[https://github.com/scottstu/scottstuCodeSamples/tree/main/Shopify-FAQ](https://github.com/scottstu/scottstuCodeSamples/tree/main/Shopify-FAQ)

<br>
Appendix:
**Metaobjects creation**

The metaobjects need to be defined first before they can be populated with the faq item data. To create a metaobject definition go to Settings/Custom data and then go to Metaobjects.

Create the following metaobjects:

*FAQ Category*

![FAQ Category Definition](/assets/img/site/FAQCategoryDefinition.png){:style="display:block; margin-left:10px; border: 2px solid #999999;"}

*FAQ Item*

![FAQ Item Definition](/assets/img/site/FAQItemDefinition.png){:style="display:block; margin-left:10px; border: 2px solid #999999;"}

