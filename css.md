1. basic
  1. styles
    ```html
    <span style="color:red">userid</span>
    ```
  
  1. class
    ```html
    <span class="user">myuserid<span>
    ```
    ```css
    .user {
      color: blue;
    }
    ```

1. load css
  1. link
    ```html
    <link rel="stylesheet" type="text/css" href="//cdn.sstatic.net/stackoverflow/all.css?v=0a13ed13b7f0">
    ```
    
  2. import [link](http://webdesign.about.com/od/beginningcss/f/css_import_link.htm)
    ```css
    @import 'custom.css';
    ```
    
  1. compare [link](http://webdesign.about.com/od/beginningcss/f/css_import_link.htm)
1. apply classes to elements
  1. id selector
    ```html
    <span id="userid">123422</span>
    ```
    ```css
    #userid {
      color: red;
    }
    ```
    
  1. tag
    ```html
    <span class="user">myuserid<span>
    ```
    ```css
    span {
      color: blue;
    }
    ```
  
  1. others
    ```css
    [foo] {
    }
    :focus {
    }
    ```

1. query selector [reference](http://www.w3schools.com/cssref/css_selectors.asp)
  1. select all
    ```css
    .foo, .bar, span {
    }
    ```
    
  1. inside
    ```css
    .foo .bar {
    }
    ```
    ```html
    <div class="foo">
      <div>
        <div class="bar">
        </div>
      </div>
    </div>
    ```
    
  1. direct child
    ```css
      .foo .bar {
        color: red;
      }
      
      .foo > .bar {
        color: green;
      }
    ```
    ```html
      <div class="foo">
        <span class="bar">text</span>
        <span class="ss">
          <span class="bar">text32</span>
        </span>
      </div>
    ```
  
  1. elememt class
    ```css
    div.foo {
      color: red;
    }
    ```
    ```html
    <div class="foo">text</div>
    ```

1. selector performance [reference](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Writing_efficient_CSS)

1. css position [link](http://www.w3schools.com/css/css_positioning.asp)
  1. fixed, usage: header, footer, button at bottom right corner
    ```css
      body {
        padding: 30px 0;
      }
      
      .header {
        background-color:red;
        position: fixed;
        top: 0;
        left: 0;
        right: 0;
        height: 30px;
      }
      
      .footer {
        background-color:green;
        position: fixed;
        bottom: 0;
        left: 0;
        right: 0;
        height: 30px;
      }
      
      .content {
        height: 1000px;
      }
      
      .fixedBtn {
        position: fixed;
        bottom: 50px;
        right: 30px;
      }
    ```
    ```html
    <body>
      <div class="header">header</div>
      <div class="content">content</div>
      <button class="fixedBtn">add</button>
      <div class="footer">footer</div>
    </body>
    ```
    
  1. absolute and fixed
    1. both don't take up spaces, need to consider z-index and padding
    1. absolute position is relative to the nearest positioned element
    1. absolute positioned elements move along while scrolling [scrollable content with fixed header](http://stackoverflow.com/questions/11891065/css-only-scrollable-table-with-fixed-headers)
  1. relative
    ```css
    .header {
      background-color:red;
      position: absolute;
      top: 200px;
      left: 0;
      right: 0;
      height: 30px;
    }
    
    .footer {
      background-color:green;
      position: relative;
      top: 100px;
      left: 0;
      right: 0;
      height: 80px;
    }
    
    .content {
      position: relative;
      height: 500px;
      overflow: auto;
    }
    ```
    ```html
    <body>
      <div class="content">
        <div class="header">header</div>
        <div class="footer">footer</div>
          content1<br>
          content2<br>
          content3<br>
          content4<br>
          content5<br>
          content6<br>
          content7<br>
          content8<br>
          content9<br>
          content0<br>
          contenta<br>
          contentb<br>
          contentc<br>
          contentd<br>
          contente<br>
      </div>
    </body>
    ```
    
  1. static
    1. default value
    1. not affected by top, bottom, left, right
1. boxmodel [reference](http://www.w3schools.com/css/css_boxmodel.asp)
  1. margin/padding
  1. width/height is content's width/height
  1. boundary of background color
  1. box-sizing: border-box;
    1. used in normanalize
    1. used in forms
1. display
  1. inline
  1. block
  1. inline-block
  1. none
    1. vs visibility
      1. space
      1. background image loading
      1. opacity: 0, top: -99999px, clip, set size to 0
      1. focusable
  1. [flexbox model](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Using_CSS_flexible_boxes)
1. [vertical align](https://css-tricks.com/centering-css-complete-guide/)
1. pseudo element
  1. ::before/::after
    1. : for labels
  1. ::selection
  1. ::first-letter/::first-line
1. [pseudo class](https://developer.mozilla.org/en-US/docs/Web/CSS/pseudo-classes)
  1. :first-child, :last-child, :only-child
  1. :nth-child()
  1. :hover, :focus
1. CSS3
  1. rounded corner/circle
  1. text overflow, word wrap
  1. Gradients
  1. shadow
  1. css functions
    1. calc()
    
      ```css
      #div1 {
          position: absolute;
          left: 50px;
          width: calc(100% - 100px);
          border: 1px solid black;
          background-color: yellow;
          padding: 5px;
          text-align: center;
      }
      ```

  1. [filter](https://developer.mozilla.org/en/docs/Web/CSS/filter)
  1. animation
  1. [media query](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries)
    1. media type, screen, print
    1. width
      ```css
      @media (min-width: 700px) and (orientation: landscape) { ... }
      ```
      
    1. device width
    1. resolution
    
      ```css
      @media print and (min-resolution: 300dpi) { ... }
      /* To replace the old (min-device-pixel-ratio: 2) */
      /* only screen and (min-device-pixel-ratio: 2) */
      @media screen and (min-resolution: 2dppx) { ... }
      ```

1. add/remove css
  1. angularjs, should be done in directive
    ```javascript
    var element = angular.element(document.getElementById('id'));
    element.addClass(...);
    element.hasClass(...);
    element.removeClass(...);
    element.toggleClass(...);
    ```
    ```html
    <p ng-class="style">Using String Syntax</p>
    <p ng-class="[style1, style2, style3]">Using Array Syntax</p>
    ```
    
  1. extjs
    ```javascript
    var element = Ext.get('id');
    var element = Ext.fly('id');
    element.addCls('cls');
    element.hasCls('cls');
    element.removeCls('cls');
    element.toggleCls('cls');
    element.radioCls('cls');
    element.addClsOnClick('cls');
    element.addClsOnFocus('cls');
    element.addClsOnOver('cls');
    // Ext.getCmp();
    // Ext.getDom();
    ```
    ```javascript
    var imageTpl = new Ext.XTemplate(
        '<tpl for=".">',
            '<div style="margin-bottom: 10px;" class="thumb-wrap {cls}">',
              '<img src="{src}" />',
              '<br/><span>{caption}</span>',
            '</div>',
        '</tpl>'
    );
    ```

1. CSS
	1. Style

			<div style="font-size: 10px;"></div>
	
	1. Seletor	
		1. simple selector, id, class, tag, attribute
				
				<span id="id">select by id<.span>
				#id {...}

				<span class="clsName">select by class</span>
				clsName {...}

				<div>select by tag</div>
				div {...}

				<div attr="attr">select by attribute</div>
				[attr] {...}
		
		1. universal

				* {...}
		
		1. combinateion

				<!-- select by group -->
				<div>test div</div>
				<span>test span</span>
				div, span {...}

				<!-- select by direct child -->
				<li>
					<button>click me</button>
				</li>
				li>button {...}
				
				<!-- select by descendant -->
				<li>
					<div>
						<button>click me</button>
					</div>
				</li>
				li button {...}
				
				<!-- select by sibling -->
				<div></div>
				<span></span>
				div+span {...}
	
		1. pseudo class

				a:link, a:visted, a:hover, a:active
				button:hover
				:first-child, :last-child
				
				:nth-child(), :nth-last-child(), :only-child
				:not()
				:enabled, :disabled, :checked
				
		1. pseudo element

				::after
				::before
				::first-letter
				::first-line
				::selection
	
	1. Javascript
			
			element.querySelector('div.clsName');
			element.querySelectorAll('div,span');

			angular.element().css()
							 .addClass()
							 .removeClass();
								
			Ext.dom.Element.setStyle()
						   .addCls()
						   .removeCls();
			
	1. box model
		1. [http://www.w3schools.com/css/css_boxmodel.asp](http://www.w3schools.com/css/css_boxmodel.asp)
		1. [https://developer.mozilla.org/en-US/docs/Web/CSS/box_model](https://developer.mozilla.org/en-US/docs/Web/CSS/box_model)
	1. CSS image
		1. background vs img vs content [http://stackoverflow.com/questions/492809/when-to-use-img-vs-css-background-image](http://stackoverflow.com/questions/492809/when-to-use-img-vs-css-background-image)
		1. sprites
		1. replacement (pros & cons)
			1. unicode code [http://unicode-table.com/en/](http://unicode-table.com/en/)
					
					p::after {
					   content: '\2930';
					}

			1. font [http://fortawesome.github.io/Font-Awesome/](http://fortawesome.github.io/Font-Awesome/)
			1. css3

					.arrow-up {
						width: 0; 
						height: 0; 
						border-left: 5px solid transparent;
						border-right: 5px solid transparent;
						
						border-bottom: 5px solid black;
					}
			
				[android logo](https://developer.cdn.mozilla.net/media/uploads/demos/M/d/MdAshrafMalik/e03f62ad7a10045e9b8f6b9243d157ff/css3-android-animate_1412954303_demo_package/index.html)
			
			1. svg [https://css-tricks.com/using-svg/](https://css-tricks.com/using-svg/)
			1. canvas
	
	1. CSS3 [https://css-tricks.com/snippets/css/](https://css-tricks.com/snippets/css/)
		1. google font [https://css-tricks.com/snippets/css/basics-of-google-font-api/](https://css-tricks.com/snippets/css/basics-of-google-font-api/)
		1. gradients 
			[background](https://css-tricks.com/css3-gradients/)
			[text](https://css-tricks.com/snippets/css/gradient-text/)
		1. border-radius
		1. Animation
		1. Media queries
		1. Many others

1. What is the difference between Normalize.css and Reset CSS?
  1. CSS resets aim to remove all built-in browser styling. Standard elements like H1-6, p, strong, em, et cetera end up looking exactly alike, having no decoration at all. You're then supposed to add all decoration yourself.
  1. Normalize CSS aims to make built-in browser styling consistent across browsers. Elements like H1-6 will appear bold, larger et cetera in a consistent way across browsers. You're then supposed to add only the difference in decoration your design needs.

1. [https://css-tricks.com/centering-css-complete-guide/](https://css-tricks.com/centering-css-complete-guide/)
