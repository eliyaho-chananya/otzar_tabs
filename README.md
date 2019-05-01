#  What is otzar-tabs?
Simplified, customizable tabs otzar-tabs is a tab component which simplifies the usage of tabs and their customization

[Video Part 1](https://prod.otzar.tech/otzar_tabs/part_1.wmv)
[Video Part 2](https://prod.otzar.tech/otzar_tabs/part_2.wmv)
## Demo

you can see the demo [here](https://cdn.otzar.tech/otzar_tabs/example.html)
# How to use:

```html
<otzartabs id="tabs" ref="myTabs">
            <tabitem is_active=1>Demo 1</tabitem>
            <tabitem>Demo 2</tabitem>
            <tabitem>Demo 3</tabitem>
</otzartabs>
```

## Installation

You can install the package via [npm](https://www.npmjs.com)

`npm install otzar-tabs --save`

or use the cdn

```html
<script src="https://cdn.otzar.tech/otzar_tabs/otzar_tabs.min.js"></script>
```

**You need to add this component to your app. either by vue.use or other methods**

## Events

`tab_click` is a [CustomEvent](https://developer.mozilla.org/en-US/docs/Web/API/CustomEvent/CustomEvent) JS. which get triggred when the tab is clicked. the otzartabs is the DOM element who triggred the event.

for example. if you want to know when the tab is clicked and which tab is it.
````javascript
//print the tab_item DOM element to the console
otzartabs_obj.addEventListener("tab_click", function(e) { console.log(e.detail) });

//JQUERY Example
$(otzartabs_obj).on("tab_click", function() {
	//DO SOME STUFF
});
````

## Methods
| Name|      Description|  
|----------|:-------------:|
| addTab(tabText:string,tabId:string) |  Add new tab_item 
| removeTab(tabId:string) |    Remove Exsiting tab_item by Id   
| setDirection(rtl=true:bool) | set the RTL/LTR directions 

you can access this methods 
```js
{APP_VAR}.$refs.{MY_REF_NAME}.{METHOD_NAME}
```
for example. 
```js
//Add new tab
myapp.$refs.myTabs.addTab("New Tab","ID_1")
//Remove Tab
myapp.$refs.myTabs.addTab("ID_1")
//Set the direction to ltr (DEFAULT = rtl)
myapp.$refs.myTabs.setDirection(false)
```

## Styles-sheets

You can apply your own css to each of the parts in this componenet
You have the following three classess
| Name|      Description|  
|----------|:-------------:|
| tab_header |  apply to all of the tab_items
| tab_item|    tab_item class  
| tab_content | only the content your add to tab_item

for example to change the buttons colors (and the borders colors too)  you can 
```css
.tab_item{
	fill:black,
	stroke:white
}
```
**i use `fill` and `stroke` props because the tbs drawing by svg**

## Pictures
![Example](https://cdn.otzar.tech/otzar_tabs/demo_rtl.png)

