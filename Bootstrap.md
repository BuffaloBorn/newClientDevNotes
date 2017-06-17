## Bootstrap 4 Rapid Web Development Framework (HTML, CSS and JavaScript)

#### Useful websites to assist in layout design

1. [Bootply](http://bootply.com)  
2. [Layoutit](http://layoutit.com)
3. [Boottheme](http://boottheme.com)
4. [Bootswatch](http://bootswatch.com)
5. [Twitter Bootstrap Button Generator](http://www.plugolabs.com/twitter-bootstrap-button-generator/)
6. [Bootsnipp](https://bootsnipp.com/)

### Browser Compatablity 

It good to review the Bootstraps compatablty  site

#### Structure of Bootstrap

Check you status for what browsers are using your application the most

```html 
<!DOCTYPE html>  <!-- indicates that this file is a HMTL 5 documemt -->
<html lang="en"> <!-- tells the browser excepted type of  language  -->
    <head>
        <!-- Required meta tags always come first -->
        <meta charset="utf-8"> <!-- tells browser what type character set render -->
        <!-- help scale the page to the device in which you are viewing your page on -->
        <meta name="viewport" content="width=device-width, initial-scale-1, shrink-to-fit=no">
         <!-- help force IE 8 in the latest rendering mode plus IE 8 backwards compatiable  -->
        <meta http-equiv="x-ua-compatible" content="ie=edge">
        <link rel="stylesheet" href="../../stylesheet/bootstrap.min.css">
    </head>
    <body>
        <!--
                It's good best bottom because we want the DOM tags to be rendered before jquery and bootstrap javascript can interact with it 
        -->
        <!-- jQuery first, then Bootstrap JS.-->
        <script src="../../javascript/jquery.min.js"/>
        <script src="../../javascript/bootstrap.min.js"/>
    </body>
</html>
```

Bootstrap Container

```html

    ...
    <link rel="stylesheet" href="custom_style.css"> <!-- custom css code is placed in this file -->
    </head>
<body>
    <div = "container-fluid"> <!-- will use the entire page width -->
    
    </div>
    <div = "container"> <!-- will use breakpoints base on bootstrap predined grid options settings that auto centers  -->

    </div>
    
        <!-- jQuery first, then Bootstrap JS.-->
        <script src="../../javascript/jquery.min.js"/>
        <script src="../../javascript/bootstrap.min.js"/>
        <script src="../../javascript/custom_script.js"/> <!-- custom javascript code is placed in this file -->
</body>
```

### Intro to  Bootstrap Grids

Breakpoints are set by media queries. Media queries allows us to resize the amount of available pixels that browser can cover.

If you reveiw bootstrap.css, check out css directive @media

```css 
@media (min-width: 544px ){


  .col-xs-4 {
    width: ?%;
  }
  .col-sm-4 {
    width: ?%;
  }
  
  .col-md-4 {
    width: ?%;
  }
  
  .col-lg-4 {
    width: ?%;
  }

  .col-xl-4 {
    width: ?%;
  }
}
``` 

1. -col-xs- = (extra small) - regardless how small the sreen the grid will always show column  
2. -col-sm- = (small)
3. -col-md- = (medium)
4. -col-lg- = (large)
5. -col-xl- = (extra large)

### Working with Grid

