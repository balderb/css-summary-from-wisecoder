# css-summary-from-wisecoder
css summary from wisecoder

@charset "UTF-8"; /* Required to prevent textual content problems */
@import "url.css"; /* Will import another stylesheet into the current one */
@media (min-width: 30em) { body { background-color: blue; } /* Media Query, VP > 30em, BGcolor blue */
}
/* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/At-rule */

/*--------------------------------------------------------------------------------------------------------*/
/*                      @-RULES, AT RULES are placed at the TOP of the CSS DOCUMENT!                      */
/*--------------------------------------------------------------------------------------------------------*/



/*--------------------------------------------------------------------------------------------------------*/
CONSIDERATIONS /* Things to consider before designing the project */
/*--------------------------------------------------------------------------------------------------------*/

AUDIENCE /* Accessibility needs, what browsers (old/new), what devices (big small) */
    /* Don't worry about the 1% using an old internet explorer */
    /* Care for people with accessibility needs, audio & visual, important */
    /* ANALYSE: http://gs.statcounter.com/ */

FEATURE-SUPPORT /* Are the features I want to implement supported on the audiences browsers/devices? */
    /* Understanding your audience and their technology can puts you in a good place to create */
    /* CHECK COMPATIBILITY: https://caniuse.com/ */

DESIGN /* Structure your page according to the NORMAL FLOW */
    /* This helps for making the site accessible for people with older browsers / Access needs */
    /* DEFENSIVE: "looks great on new browsers", but still usuable at basic leve on old browsers */

FALLBACKS /* CSS rules that will apply if browser doesn't support the newer features */



/*--------------------------------------------------------------------------------------------------------*/
STYLESHEET /* CSS aka CASCADING STYLE SHEET */
/*--------------------------------------------------------------------------------------------------------*/

/* Understanding how CASCADING works is key to understand how CSS works */
/* In simple words, the order of the css rules matter. */
/* If we have 2 rules with EQUAL specificity, the last RULE is the strongest and will be used */

EXTERNAL STYLESHEET
/* We use external styling so that we can style multiple web pages with one stylesheet */
/* All CSS Rules are written in an external ".css" file. */
/* A link is placed inside the <head> element of the HTML file, by using the <link> element */
/* Example: <link rel="stylesheet" href="styles.css"> */
/* USE: MOST USEFUL, most common, maintenance friendly.*/

INTERNAL STYLESHEET
/* We use internal styling to individually style a single web page */
/* All CSS Rules are written inside the <head> element of the HTML file, inside the <style> element */
/* Example: <style>CSS RULES</style> */
/* USE: LESS EFFICIENT, maintenance unfriendly, can be useful with a restricted ContentManagmSystem */

INLINE STYLING
/* We use inline styling to style a single HTML element */
/* All CSS Rules are written within the style="" attribute */
/* Example: <p style="color:red;">Hello worlds</p> */
/* USE: AVOID when possible, code readability, can be useful with a restricted CMS */

ERROR HANDLING /* Typo's', older browsers, CSS will ignore these RULES or DECLARATIONS */
/* If a browser encounters a SELECTOR that it can't read, it skips the whole RULE */
/* If a browser encounters a DECLARATION that it can't read, it skips the whole DECLARATION */

/* USEFUL: First write the OLD css, then the NEW css, CASCADE will use the last RULE if possible */
/* The OLD css will be used if the NEW css can't be read by the browser.
If the NEW css can be read, it will use the NEW css to style the element */

/*----------*/
/* CSS RULE */
/*----------*/
CSS-RULE-STRUCTURE /* One rule can have many selectors and many declarations */
    h1                /* Selector */ 
    {
        color:blue; /* Declaration = Property & Value */ 
    }

    SELECTOR     /* Select the element(s) we want to style */
    DECLARATION  /* Consists of a PROPERTY a ":" a VALUE and a ";" */
    PROPERTY     /* CSS Property we want to style */
    VALUE        /* Value we want to give the CSS property */



/*--------------------------------------------------------------------------------------------------------*/
ORGANISING THE STYLESHEET
/*--------------------------------------------------------------------------------------------------------*/
    
TIPS
/* CODE STYLING GUIDE, if project has one, always follow it over personal prefference */
/* CONSISTENCY, Spaces, ID/class names, colors, rule structure, be consistent */
/* READABLE, make your CSS readable, New line for every rule for example */
/* COMMENT, Helps you when you have been away for a while, or other developers */
    /* Add a comment before each new segment, when using fallback rules, etc... */
/* LOGICAL SECTIONS, create sections inside your css which are logical */
/* AVOID overly-specific selectors, will lead to having lots of duplicate code */
/* BREAK LARGE STYLESHEETS into multiple smaller ones, CASCADE works also on @rules */


CSS METHODOLOGIES /* No need to invent a new way of writing, use a popular one that exists already */
/* Can be DISADVANTAGEOUS for SMALL projects, can be VERY advantageous for BIG projects! */
    OOCSS /* Obejct Oriented Cascading Style Sheet, https://github.com/stubbornella/oocss/wiki */
        /* Idea is to sepparate your css into re-usable objects, can be used anywhere in your site */
        /* Example: Media Objects */
    BEM /* Block Element Modifier, https://css-tricks.com/bem-101/ */
        /* BLOCK: Standalone entity, like a button, logo, menu */
        /* ELEMENT: List item or a title, that is tied to the block it is in */
        /* MODIFIER: A flag on a block or element that changes styling or behaviour */
        /* DASHES & UNDERSCORES: Uses a lot of dashes and underscores in the class names */
        /* BEM Naming Convention http://getbem.com/naming/ */
        /* Widely used in larger web projects */
    SMACSS /* Scalable and Modular Architecture for CSS http://smacss.com/ */
    ITCSS /* A Sane, Scalable, Managed CSS architecture from CSS Wizardry https://itcss.io/ */
    ACSS /* Atomic CSS https://acss.io/ */


SYSTEMS /* We can take a slightly more programmatic approach by using pre-processors */
    PRE-PROCESSOR /* Takes your raw CSS code turns it into a stylesheet */
        SASS /* Most popular pre-processor, https://sass-lang.com/guide */
        /* Use: Define variable color, processor changes color to the variable in each place in the SS */
    /* CSS can define variables natively, making sass less important nowadays */
    /* https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties */

    POST-PROCESSOR /* Compiles your finished stylesheet, Strips out unnecassary stuff, loads faster */
        CSSNANO /* Post-processor, https://cssnano.co/ */



/*--------------------------------------------------------------------------------------------------------*/
CASCADING /* The order of CSS rules matter */
/*--------------------------------------------------------------------------------------------------------*/

/* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/Cascade */

/* If we have 2 rules with EQUAL specificity, the last RULE is the strongest and will be used */
    h1 { color: red; } /* This rule is ignored */
    h1 { color: blue; } /* This rule is used, equal specificity, comes last */

INHERITANCE /* Child elements will inherit the parents styling, unless it has been styled specifically */
/* Some properties don't inherit, it would be frustrating, Example: border:1px; */

SPECIFICITY /* How the browser decides to style an element, when element has multiple selector rules */
/* A CLASS selector is more specific than an ELEMENT selector, so CLASS selector is stronger */
    .class { color: red; } /* More specific, gets a higher score */
    h1 { color: blue; } /* Less specific, gets a lower score */

	CALCULATE SPECIFICITY /* this isn't exactly how a browser does it, but it comes close */
    Thousands /* 1000:  Score 1 for each: INLINE selector by using the <style> attribute */
    Hundreds  /* 100:   Score 1 for each: ID selector */
    Tens      /* 10:    Score 1 for each: CLASS selector, ATTRIBUTE selector, PSEUDO-CLASS selector */
    Ones      /* 1:     Score 1 for each: ELEMENT selector, PSEUDO-ELEMENT selector */
    None /* Selector (*), combinators (+, >, ~, ' '), pseudo-class (:not) have no effect on specificity */
    /* <style>                                  1000, Inline:1000 */
    /* #identifier                              0100, id:100 */
    /* li > a[href*="en-US"] > .inline-warning	0022, Li:1, a:1, []:10, .class:10 */
    /* h1 + p::first-letter                 	0003, h1:1, p:1, ::psuedo-element:1 */
    /* h1                                       0001, h1:1 */
	
	IMPORTANT /* DONT USE IT! This makes a Declaration the most specific thing. Overrides the cascade */
        li { top:0 !important; } /* Makes this the most specific Declaration */



/*--------------------------------------------------------------------------------------------------------*/
SELECTORS AND COMBINATORS /* Ways of chosing which element or group of elements we want to style */
/*--------------------------------------------------------------------------------------------------------*/

/* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors */

UNIVERSAL /* "*" Select all elements in a document, can be chained with other selectors */
    * /* Select all elements in the document and apply the Declaration to all */
    article *:first-child /* Selects any element which is the first child of an <article> */

TYPE /* "element" Select elements based on their html TYPE */
    div, p, h1, header

CLASS /* ".className" Select elements based on their CLASS */
    .class, .class2 /* CLASS: Targets all elements with the class="class". Starts with a "." */

ID /* "#idName" Select elements based on their ID */
/* NOTE: In most cases it is preferable to add a class to the element rather than use an ID */
    #id, #id2, #id3 /* ID: Targets all elements with the id="ID". Start with a "#" */

ATTRIBUTE
    PRESENCE /* Select elements based on presence of an attribute */
        a[title] /* Select all elements with a title attribute */

    VALUE /* Select elements based on an attribute value */
        a[href="url"] /* Select all elements with a "href" attribute containing a value "url" */

    SUBSTRING MATCHING
        li[class^="a"] /* Matches any attribute value which starts with "a" */
        li[class$="a"] /* Matches any attribute value that ends with "a" */
        li[class*="a"] /* Matches any attribute value where "a" appears anywhere in the string */
    
    CASE INSENSITIVE
        li[class*="A" i] /* Match attribute values case-INSENSITIVELY you can use the value "i" */

PSEUDO CLASS /* "type:pscl" Select elements that are in a certain state */
/* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes */
    a:hover /* ":hover" psuedoclass styles an element when a mouse hovers over it */

PSEUDO ELEMENTS /* "type::psele" Styles a certain part of an element, acts like html was added */
/* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements */
    p::first-line /* Styles the first line of every p element. Acts like a span */
    p::before { content:"text" } /* "text" printed BEFORE other content */


DESCENDANT COMBINATOR /* " " Targets all "SEL2" descendant elements that have a "SEL1" ancestor */
    main p /* Selects all <p> elements that have a <main> ancestor element */

CHILD COMBINATOR /* ">" Targets all "SEL2" that are direct children of our "SEL1" parent */
    main > p /* Select all <p> elements that are direct childeren of the <main> element */

ADJACENT SIBLING COMBINATOR 
/* "+" Select element that comes DIRECTLY after "SEL1" and have the SAME parent element */
    h1 + p /* Style first <p>, that is directly after <h1> on the same hierarchy */
    h1+ul+p /* Style first <p>, that is directly after <ul>, that is directly after <h1> */

GENERAL SIBLING COMBINATOR
/* "~" Select the element that comes AFTER the "SEL1" and has the SAME parent element */
/* Does NOT have to be DIRECTLY after the "SEL1" element as with an adjecent sibl combi*/
    h1 ~ p /* Style first <p>, that is somewhere after <h1> on the same hierarchy */

SELECTORS and COMBINATORS /* CARE! Big selector lists are hard to reuse and manage */
    li.class
        /* Targets any li-element that has a class="class" */
    article p span
        /* selects any <span> that is inside a <p>, which is inside an <article>  */
    h1 + ul + p
        /* selects any <p> that comes directly after a <ul>, which comes directly after an <h1>  */
    body h1 + p .class
        /* This will style any element with a class of "class", which is inside a <p>, 
        which comes just after an <h1>, which is inside a <body> */



/*--------------------------------------------------------------------------------------------------------*/
DECLARATIONS /* Style element, Has a PROPERTY and a VALUE, sepparated by a ":", and ends with ";" */
/*--------------------------------------------------------------------------------------------------------*/

/* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/Syntax */

PROPERTY /* The specific CSS PROPERTY we want to style */
    /* https://developer.mozilla.org/en-US/docs/Web/CSS/Reference find all properties here */

VALUE /* A value is based on the property, most values are simple keywords or numeric values */
    SHORTHANDS /* Shorthand properties set several values in a single line */
    /* WARNING: A value not specified in CSS shorthand reverts to its initial value */
    /* This means that an omission in a CSS shorthand can override previously set values */
        p { padding: 10px 15px 15px 5px; } /* SHORT 1 */
        p { padding-top:10px; padding-right:15px; padding-bottom:15px; padding-left:5px; } /* LONG 1 */

        p { border: 1px red; } /* SHORTHAND 1 */
        p {border-top: 1px; border-right: 1px; border-bottom: 1px; border-left: 1px; border-color: red;}
    

    INHERIT /* This property value inherits its value from the parent */
    /* This "turns on inheritance" for this property */
        li {color:inherit;} /* Color will be the color value of the parent ul,ol,dl or higher up... */
    
    INITIAL /* Sets the property value, applied to the element, to the initial value of that property */
        li {color:initial;} /* Color is the value of the initial property value (ex. black html text) */

    UNSET /* Resets the property value to it's natural value. */
    /* If a property is naturally inherited, it acts like INHERIT, otherwise acts like INITIAL */
        li {all:unset;} /* Resets all css rules to default */



/*--------------------------------------------------------------------------------------------------------*/
DATATYPES aka VALUES /* All data-types we can use in conjunction with certain properties */
/*--------------------------------------------------------------------------------------------------------*/

INTEGERS /* Whole number: 1024 ; -55 ; ... */    
NUMBERS /* Decimal: 0.25 ; -1.2 ; ... */    
PERCENTAGES /* Always relative to another value, usually the parents property value */

DIMENSIONS /* A number with a unit attached to it: 45deg ; 5s ; 10px ; ... */
    LENGTHS /* Most frequent numeric type: 4px ; 40pt ; 4em ; ... */
        ABSOLUTE /* They are not relative to anything else, always the same size */
            cm, mm, in, pc, pt, px /* Most common value is px to use in web design */
        
        RELATIVE /* Always relative to something else, can change dynamically, scaling */
            em /* Frequent use, Means "my parents elements font size", Nesting grows/shrinks size */
            rem /* Frequent use, Means "the root element's font size", Nesting keeps size equal */
            ex /* x-height of the element's font */
            ch /* The advance measure (width) of the glyph "0" of the element's font */
            lh /* Line height of the element */
            vw /* 1% of the viewport's width */
            vh /* 1% of the viewport's height */
            vmin /* 1% of the viewport's smaller dimension */
            vmax /* 1% of the viewport's larger dimension */

COLORS /* 3 Color types to be used in CSS */
/* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/color_value */
/* RGBA is recommended, All is possible, Try to be consistent in your choice */
    KEYWORD /* String, less versitile, Ex: red, tan, snow, thisle, blue, ... */
    HEX/* "#" followed by 6 hexnumbers (0123456789abcdef), more versitile, Ex: #02af56 */
    RGB /* Easier than HEX, Is a function "rgb()", Red-Green-Blue, 0-255 R, 0-255 G, 0-255 B */
    RGBA /* Same as RGB, but has 4th channel, ALPHA channel, controls opacity, value 0-1 */
    HSL /* Hue Saturation Lightness, For designers, less supported, 0-360 H, 0-100% S, 0-100% L */
    HSLA /* Same as HSL, but has 4th channel, ALPHA channel, controls opacity, value 0-1 */

IMAGES /* Used when an image is a value, function url(), function gradient() */
/* https://developer.mozilla.org/en-US/docs/Web/CSS/image */
    p { background-image: url(img); }
    p { background-image: linear-gradient(90deg, rgba(119,0,255,1) 39%, rgba(0,212,255,1) 100%); }

POSITION /* Set of 2D coordinates, Top-right-bottom-left-center, Length offsets from the top left */
    p { background-position: right 40px; } /* Positioned on the right side, 40px from the top */

IDENTIFIERS aka KEYWORDS /* They are not "quoted" but css still identifies them as words, strings */
    p { background-color: burlywood; } /* Unquoted string, color */

STRINGS /* When spcifying general content, we use "quotated" strings */
    p::before { content: "This string comes before the paragraphs text"; }
    p::after { content: "This string comes after the paragraphs text"; }

FUNCTIONS /* There are some values which take the form of a function */
/* Reusable section of code, Can run multiple times, Helps developer with repetitive tasks */
/* FUNCTIONS: Calc(); url(); hsl(); rgba(); ... */
    CALC /* Gives ability to do simple calculations inside CSS */
    p { width: calc(90% - 30px); } /* <p> Width will be 90% of it's full size minus 30px */
    TRANSORM /* Gives ability to rotate elements */
    p { transform: rotate(0.8turn) } /* will rotate the selected element 0.8turn */

        

/*--------------------------------------------------------------------------------------------------------*/
BOX-MODEL /* How does the box behave in terms of page flow, and in relation to other boxes on the page */
/*--------------------------------------------------------------------------------------------------------*/

BOX-PARTS /* The box MODEL defines how different parts of the box work together */
    CONTENT-BOX /* Area where content is displayed, defined by WIDTH & HEIGHT */
        .box { width: 100px; height: 200px; }
        
    PADDING-BOX /* Wraps around the CONTENT as whitespace. */
    /* Longhand */
        padding-top, padding-right, padding-bottom, padding-left
    /* Shorthand */
        .box { padding: 10px; } /* All padding is 10px thick */
        .box { padding: 1px 2px 3px 4px; } /* Top, Right, Bottom, Left */
        
    BORDER-BOX /* Wraps CONTENT and any PADDING. Style with BORDER and related properties */
    /* Longhand */
        border-top, border-right, border-bottom, border-left, border-width, border-style, border-color
    /* Shorthand */
        .box { border: 1px solid #333333; } /* Set all borders with 1 line */
        .box { border-top: 5px dotted green; } /* Target 1 specific border */

    MARGIN-BOX /* Wraps the BOX as whitespace. Pushes other elements away from the box, + & - values possible */
    /* Longhand */
        margin-top, margin-right, margin-bottom, margin-left
    /* Shorthand */
        .box { margin: 10px; } /* All margin is 10px thick */
        .box { margin: 1px 2px 3px 4px; } /* Top, Right, Bottom, Left */

        MARGIN COLLAPSING
        /* If 2 positive margins touch, they callapse into 1 margin, the largest of the 2 */
        /* If If one or both are negative, the amount of negative value will subtract from the total */


STANDARD-BOX /* Actual size box size on page is: WIDTH or HEIGHT + 2xPADDING + 2xBORDER */
    /* This is the standard way browser handle boxes */
    .box { width: 350px;height: 150px;margin: 10px;padding: 25px;border: 5px solid black; }
    /* Box total WIDTH is 410px (350 + 2x25 + 2x5), Box total HEIGHT is 210px (150 + 2x25 + 2x5) */
    /* Box visually stops at its border, but margin still takes its place on the page */

ALTERNATIVE-BOX /* WIDTH/HEIGHT is the actual visible WIDTH/HEIGHT on the page */
    /* This is more easier for developers */
    .box { box-sizing: border-box; }
    /* If we want all our element boxes to behave like this we can add following css */
    html { box-sizing: border-box; } /* all htlm's children become alternative boxes */
    *, *::before, *::after { box-sizing: inherit; } /* All other elements inherit this as well */



/*--------------------------------------------------------------------------------------------------------*/
CSS LAYOUTS /* Different methods for creating page layouts (Grid / Flex / Legacy) */
/*--------------------------------------------------------------------------------------------------------*/

NORMAL-FLOW /* The default page flow the browser choses if we do nothing to control the page layout */
/* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flow_Layout */
    /* HTML is displayed in the exact order in which it appears in the source code */
    /* Elements are laid out by taking the content, adding padding, border & margin to it */
    /* BLOCK, WIDTH is 100% of the parent, HEIGHT is based on how tall the content is */
    /* INLINE, WIDTH/HEIGHT is based on its content, therefor W/H can't be changed inline */
    /* Based on TEXT-WRITING mode, blocks are laid out Horizontaly from TOP to BOTTOM by default */
    /* MARGIN COLLAPSE when 2 margins touch, small margin dissapears, big margin stays */

DISPLAY /* Sets whether element is block or inline, and to set it's inner layout */
/* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/display */

    /*----------------------------------------------------------------------------*/
    /* DISPLAY, OUTER PROPERTIES, Target the OUTSIDE of the box-container element */
    /*----------------------------------------------------------------------------*/
    BLOCK /* This is the default value for EX: <h1>, <p>, <li> ... */
        .box { display: block; }
    /* The box WILL BREAK onto a new line */
    /* The box EXTENDS in inline direction, in most cases takes up 100% of its container width */
    /* The box' WIDTH and HEIGHT properties WILL APPLY */
    /* PADDING, MARGIN and BORDER will cause OTHER elements to be PUSHED AWAY from the box */

    INLINE /* This is the default value for EX: <a>, <span>, <em>, <strong>, ... */
        .box { display: inline; }
    /* The box will NOT BREAK onto a new line*/
    /* The box' WIDTH and HEIGHT properties will NOT APPLY */
    /* VERTICAL padding, margins, and borders will apply, but WON'T PUSH other inline boxes AWAY */
    /* HORIZONTAL padding, margins, and borders will apply, and WILL PUSH other inline boxes AWAY */

    INLINE-BLOCK /* Creates a middle ground between block and inline */
        .box { display: inline-block; }
    /* The box will NOT BREAK onto a new line*/
    /* The box' WIDTH and HEIGHT properties WILL APPLY, but WILL become LARGER than its content */
    /* PADDING, MARGIN and BORDER will cause OTHER elements to be PUSHED AWAY from the box */
    /* USE: Give LINKS a larger hit area, onhover <a> will pop out and respect the padding */


    /*-------------------------------------------------------------------------*/
    /* DISPLAY, INNER PROPERTIES, Target the elements INSIDE the box-container */
    /*-------------------------------------------------------------------------*/   
    
    /*------*/
    /* GRID */
    /*------*/
    GRID /* A set of intersecting Vertical & Horizontal lines (ROWS/COLUMNS) sepparated by GAPS (gutters) */
    /* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/grid */
        /* Apply to PARENT element, all DIRECT children will become GRID items */
        .box { display: grid; }
    
        
    /* GRID COLUMN PLACEMENT */
        GRID-TEMPLATE-COLUMNS /* EXPLICIT ROW GRID, Columns are manually sized */
        /* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-columns */
            .box { grid-template-columns: repeat(auto-fill, minmax(200px, 1fr)); } /* RESPONSIVE grid */
            .box { grid-template-columns: repeat(3, 1fr 2fr); } /* REPEAT function */
            .box { grid-template-columns: 1fr 1fr; } /* FLEXIBLE, Fraction based width */
            .box { grid-template-columns: 200px 200px 200px; } /* Add 3, 200px-wide, columns */
        
            GRID-AUTO-ROWS /* IMPLICIT: Rows are auto sized to hold content */
            /* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/grid-auto-rows */
                .box { grid-auto-rows: 200px; } /* All rows will be 200px tall, Care for content overflow */
                .box { grid-auto-rows: minmax(100px, auto); } /* RESPONSIVE, tackles potential overflow */

                
    /* GRID ROW PLACEMENT */
        GRID-TEMPLATE-ROWS /* EXPLICIT ROW GRID, Rows are manually sized */
        /* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-rows */
            .box { grid-template-rows: repeat(auto-fill, 300px); } /* RESPONSIVE grid */
            .box { grid-template-rows: repeat(3, 1fr 2fr); } /* REPEAT function */
            .box { grid-template-rows: 1fr 1fr; } /* FLEXIBLE, Fraction based height */
            .box { grid-template-rows: 200px 200px 200px; } /* Add 3, 200px-wide, rows */
        
            GRID-AUTO-COLUMNS /* IMPLICIT: Columns are auto sized to hold content */
            /* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/grid-auto-columns */
                .box { grid-auto-columns: 100px; } /* All columns will be 100px wide, Care for overflow */
                .box { grid-auto-columns: minmax(100px, auto); } /* RESPONSIVE, tackles potential overflow */
     
                
    /* GRID LINE PLACEMENT */
        GRID-COLUMN 
        /* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/grid-column */
            .item { grid-column: 1/3; } /* SHORTHAND, Start/End separated by a forward slash "/" */
                .item { grid-column-start: 1; } /* Element starts in our FIRST COLUMN */
                .item { grid-column-end: 3; } /* Element ends in our THIRD COLUMN */
        GRID-ROW
        /* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/grid-row */
            .item { grid-row: 1/2; } /* SHORTHAND, Start/End separated by a forward slash "/" */
                .item { grid-row-start: 1; } /* Element starts in our FIRST ROW */
                .item { grid-row-end: 2; } /* Element ends in our SECOND ROW */
            /* We can use "-1" to target END of the column/row line, only on IMPLICIT grid */


    /* GRID NAME PLACEMENT */
        GRID-TEMPLATE-AREAS
        /* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-areas */
            .box { grid-template-areas: "head head" "main bar" "foot foot" ; } /* Make name grid */
            .item1 { grid-area: head; } /* CHILD property, Element placed on Col1-Row1 to Col2-Row1 */
            .item2 { grid-area: bar; } /* CHILD property, Element placed on Col2-Row2 */
            /* Rules */
                /* Every cell of the grid has to be filled, Use a "." to leave a cell empty */
                /* Repeat the name twice to span accross 2 cells */
                /* Areas must be rectangular, Can't be L-shaped for example */
                /* Areas can't be repeated in different locations */ 
  
                
    /* GRID GAP aka GUTTERS */    
        GAP /* SHORTHAND, To set gap space between BOTH columns & rows at once */
        /* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/gap */
            .box { gap: 20px; }
            COLUMN-GAP /* To create GAPS between our COLUMN tracks */
                .box { row-gap: 10px; }
            ROW-GAP /* To create GAPS between our ROW tracks */
                .box { row-gap: 10px; }


    /* RESPONSIVE GRID */
        /* Create as many columns/rows, with certain width/height, as will fit in container */
        REPEAT /* Function helps creating (responsive) grids */
        /* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/repeat */
            AUTO-FILL /* Fills its container with as many sized rows/columns as possible */
                .box { grid-template-columns: repeat(auto-fill, minmax(auto, 1fr)); }
            AUTO-FIT /* Fills its container, but collapses empty tracks to 0px */
                .box { grid-template-columns: repeat(AUTO-FIT, minmax(auto, 1fr)); }
        
        MINMAX /* Set both min & max size value of our rows/columns */
        /* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/minmax */
            
        /* EXAMPLE */
            .container { 
                display: grid;
                grid-template-columns: repeat(auto-fill, minmax(200px, 1fr)); /* Min 200px, max 1fr wide */
                grid-auto-rows: minmax(100px, auto); /* Rows min "100px" high, max "auto" */
                grid-gap: 20px; /* Gutter-gap of 20px between all tracks */ 
            }


    /*---------*/
    /* FLEXBOX */
    /*---------*/
    FLEXBOX /* Lay elements in 1 dimension, either in a row or column */
    /* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox */
        .box { display: flex; } /* Places blocks next to each other in a container */
        .box { display: inline-flex; } /* Places inline-elements as flexible boxes */
    

    /* FLEX CONTAINER, Parent element which is the container for our flex-items */    
        FLEX-CONTAINER /* Has 2 axes, Main-axis & Cross-axis, both have a start and an end */
    
            FLEX-FLOW /* Combination of flex-direction & flex-wrap */
            /* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/flex-flow */
                /* SHORTHAND, Recommended */
                .box { flex-flow: row wrap; } /* Flex items placed on MAIN-axis, Items are being WRAPPED */
                
                /* LONGHANDS, Don't use, Unnecessary code */
                FLEX-DIRECTION /* Direction in which MAIN-axis runs in */
                /* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/flex-direction */
                    .box { flex-direction: row; } /* DEFAULT, lays items horizontally */
                    .box { flex-direction: column-reverse; } /* Reverses items horizontally */
                    .box { flex-direction: column; } /* Lays items vertically */
                    .box { flex-direction: column-reverse; } /* Reverses items vertically */   

                FLEX-WRAP /* RESPONSIVE: Wrap flex-items, Responsive behaviour when viewport becomes smaller */
                /* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/flex-wrap */    
                    .box { flex-wrap: wrap; }
            
            JUSTIFY-CONTENT /* Controls WHERE the flex items sit on the MAIN (HORIZONTAL) axis */
            /* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/justify-content */
                .box { justify-content: flex-start; } /* DEFAULT, All items sit at the start of the main axis */
                .box { justify-content: center; } /* All items sit in the center of the main axis */
    
            ALIGN-ITEMS /* Controls WHERE the flex items sit on the CROSS (VERTICAL) axis */
            /* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/align-items */
                .box { align-items: stretch; } /* DEFAULT, Stretches items to fill parent in cross axis direction */
                .box { align-items: center; } /* Intrinsic dimensions remain, Centers items along cross axis */
    
                    
    /* FLEX-ITEM, Direct child of our flex-container, has a MAIN size and a CROSS size */        
        FLEX /* Grow, Shrink item compared to other flexitems, Set minimum width of item */
        /* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/flex */
            /* SHORTHAND, Recommended */
            .item { flex: 1 1 100px; } /* Has a grow, shrink factor of 1, Item is min 100px wide */   
            
            /* LONGHANDS, Do not use, Unnecessary code */
                .item { flex-grow: 1; } /* Grow-factor, Unitless, Is compared to other items gfactor */
                /* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/flex-grow */
                .item { flex-shrink: 1; } /* Shrink-factor, Unitless, Is compared to other items sfactor */
                /* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/flex-shrink */
                .item { flex-basis: 100px; } /* Set initial main size of item */
                /* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/flex-basis */  
            
        ALIGN-SELF /* Overrides "ALIGN-ITEMS" behaviour for individual flex items */
        /* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/align-self */
            .item1 { align-self: flex-end; } /* Aligns child .item1 to the end of the CROSS axis */
                
        ORDER /* DEFAULT VALUE = 0, CHILD Prop. The order relative to the other items, their default is 0 */
        /* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/order */
            .box:nth-child(1) { order: 2; } /* Places item after items with a value smaller then 2 */
            .box:nth-child(2) { order: -1; } /* Places item BEFORE all default "0" items */
            
                
    /*--------*/
    /* FLOATS */
    /*--------*/
    FLOATS 
    /* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/float */
        /* We can float ANYTHING, not just images, Ex: drop-caps */
        .box { float: left/right; } /* Floats element to the left/right */
        .box { float: none; } /* Default value, no flaoting */
        .box { float: inherit; } /* Inherits value from parent */
        /* Any elements coming after the floating element will be wrapped around it */
        
        CLEAR /* Prevents elements, that follow our floated element, from wrapping around it */
        /* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/clear */
        .cleared { clear: left/right/both; } /* Clear items floated to the left/right/both */
        /* When we use clear, the element before our clear will not wrap around our float fully */
        
        FLOW-ROOT /* Wrap FLOAT and UNCLEARED elements in a box, fixes styling, Ex: background color */
        .box { display: flow-root; }


    /*----------*/
    /* POSITION */
    /*----------*/
    POSITION /* Displace element from where it would be placed in normal flow to somewhere else */
    /* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/position */
        
        /* Used to fine tune rather then to create your main page layout with */
        .box { position: static; } /* DEFAULT, puts element in the normal document layout flow */
        .box { position: relative; } /* Move element relative to its position, overlap possible */
        .box { position: absolute; } /* Move free from normal flow, own layer, move anywhere */
        .box { position: fixed; } /* Fixes element relative to nearest ancestor, EX: Nav menu */
        .box { position: sticky; } /* Goes from "static" to "fixed" based on defined viewport offset */
        
        T-B-L-R-M /* Position element properties, margin affects position, margin collapsing doesn't */
            .box { top: 0px; bottom: 0px; left: 0px; right: 0px; margin: 0px; } /* px, rem, em, %, ... */
        
        Z-INDEX /* Stacking order, HIGHER values ABOVE lower, z-axis, Overlap, Unitless */
        /* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/z-index */
            /* Positioned elements will ALWAYS be ABOVE non-positioned elements */
            .box { z-index: 5; }


    /*----------*/
    /* MULTICOL */
    /*----------*/
    MULTi-COL /* Multi Column Layout, Puts elements in multiple columns */
        .box { column-count: 3; } /* We want the browser to create 3 columns inside our container */
        .box { column-width: 200px; } /* We want as many 200px columns as possible inside our container */
        .box { column-gap: 20px; } /* Gap between our columns is 20px */
        .box { column-rule: 4px dotted rgb(79, 185, 227); } /* Add a dotted line between our columns */
        .box { column-span: all; } /* Will span element accros all columns, EX: Subheader */
        .box { break-inside: avoid; } /* Will prevent fragmentation of our element at column split */


    /*----------*/
    /* FALLBACK */
    /*----------*/
    FALLBACK METHODS /* LEGACY SUPPORT, Create fallbacks inside your CSS rules to support older browsers */
    /* INFO: https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Legacy_Layout_Methods */
        
        /* These methods are ALL IGNORED when an element becomes a FLEX or GRID item */
        FLOAT and CLEAR /* Are ignored when elements become FLEX/GRID items */
        display:INLINE-BLOCK /* Create column layout, Is ignored when element becomes FLEX/GRID item */
        display:TABLE /* Table Layout, */
        MULTI-COL /* Certain layouts fallback can be set with a MULTICOL layout */
        FLEXBOX /* Fallback for GRID, is older and has more browser support than grid */  
        @supports (display: grid) { .item { width: auto; } } /* Check if we have grid support */
        
        

/*--------------------------------------------------------------------------------------------------------*/
RESPONSIVE WEB-DESIGN /* Creating "fluid-like" websites for all screen-sizes is the new standard! */
/*--------------------------------------------------------------------------------------------------------*/

    FLEXIBLE GRIDS /* Responsive pages don't just change on breakpoints, they are build on flex grid */
        /* We don't have to target every possible screensize that there is, and build a pixel perfect layout */
        /* We only add a breakpoint and change the design where the page starts to look bad, */
            FLEXBOX /* Items will shrink, distribute space between items according to space in container */
            GRID /* fr unit allows the distribution of available space across grid tracks */
            MULTI-COL /* Oldest layout method, can split content in multiple columns */
    

    MEDIA QUERIES /* Allow us to run a test, and apply certain CSS for different outcomes of the test */
        /* We can test what viewport size our user has, touchscreen or mouse, ... */
        /* A stylesheet can containe multiple media queries, can be used to style anything, not only layout */
        /* The point at which a media query is introduced and the layout changes is called a BREAKPOINT */
        
        STRUCTURE
            @media media-TYPE and (media-feature-RULE) {
                /* CSS */
            }
            /* TYPE: Tells browser what type of media this is, EX: Screen, Print, ... */
            /* LOGIC: AND, OR, NOT operators */
            /* RULE: Is a test, that must be passed for our "CSS rules" to be applied */
            /* CSS: Rules that will be applied if the RULE test is passed */
            
            MEDIA-TYPES
                
                ALL /* DEFAULT, Matches ALL devices */
                PRINT /* Matches PRINTERS, and devices intended to print a page, EX: Print Preview */
                SCREEN /* Matches all devices that AREN'T matched by PRINT or SPEECH */
                SPEECH /* Matches SCREEN READERS or other devices that "read out" a page */


            MEDIA-FEATURE-RULES /* Rule that has to be passed for CSS to be applied */
                
                WIDTH and HEIGHT
                    /* MIN/MAX/WIDTH: Checks if viewport is BELOW, ABOVE or EXACT width */
                    /* MIN/MAX/HEIGHT: Checks if viewport is BELOW, ABOVE or EXACT height */
                        /* We rarely use WIDTH/HEIGHT, Since they target EXACT viewport sizes */
                    @media screen and (width: 600px) { body { color: red; } }
                        /* Makes body color red, if viewport width is EXACT 600px wide */
                    @media screen and (max-width: 400px) { body { color: blue; } }
                        /* Makes body color blue, if viewport is narrower than 400px */
                ORIENTATION /* Checks if screen orientation is PORTRAIT or LANDSCAPE */
                    /* Desktop is usually LANDSCAPE, mobiles are usually PORTRAIT */
                    @media (orientation: landscape) { body { color: purple; } }
                HOVER /* Check if user has the ability to hover over elements, Mouse? */
                    @media (hover: hover) { body { color: purple; } }
                POINTER /* Checks how user is navigating the site, can help in the design */
                    @media (pointer: fine) { body { color: rebeccapurple; } }                
                    FINE /* Mouse or trackpad navigation, user can precicely target small areas */
                    COARSE /* Finger on touchscreen navigation, create larger hit areas */
                    NONE /* Navigation with keyboard or voice */

            LOGIC /* We can combine multiple media features in 1 Query by using logical operators */
                AND /* COMBINE: IF feature 1 AND feature 2 AND feature n ARE TRUE, Exectute CSS */
                OR /* MATCH: IF feature 1 OR feature 2 OR feature n IS TRUE, Execute CSS */
                NOT /* NEGATE: IF feature 1 is NOT TRUE, Execute CSS */
                    @media not all and (orientation: landscape) { body { color: blue; } }
                    /* IF orientation is NOT LANDSCAPE, body color blue */
            
        USAGE /* Flexbox, Grid, Multicol give us ways to create flexible and responsive pages */
        /* We only use Media Queries if we can't solve our problem with our Flex,Grid,Multicol aproach */


    RESPONSIVE IMAGES /* Based on screen size we can, crop, scale, provide multiple sizes of img */
    /* Still used today, usually you will find "max-width:100%" in stylesheets */


    RESPONSIVE TYPOGRAPHY /* Changing font size based on media queries, improves screen real-estate */
    /* Example, we can use media queries for many things, not only for editing page layout */
        html { font-size: 1em; } /* Set ROOT f.size */ h1 { font-size: 2rem; } /* HEADING f.size */
        @media (min-width: 1200px) /* If screen is at least 1200px wide */
            { h1 { font-size: 4rem; } } /* Then increase <h1> size */
    /* Example, using VW to create responsive text */
    h1 { font-size: 6vw; } /* CAREFUL!! This will increase text also when zooming, we don't want that */
    h1 { font-size: calc(1.5rem + 3vw); } /* Solution to make text responsive and zoomable */


    RESPONSIVE DESIGNS
        MOBILE FIRST /* BEST! Start with SMALLEST view and add LAYOUT as viewport becomes larger */
            /* First create a simple SINGLE column layout, for narrow screen sizes (phones) */
            /* Then check for larger screen sizes and implement a multiple-column layout */
        DESKTOP FIRST /* Start with WIDEST view and add BREAKPOINTS as viewport becomes smaller */


    CHOSING BREAKPOINTS /* How to chose breakpoint */
    /* Change design where content starts to break instead of focussing on different screen sizes */
        MOZILLA-DEV-TOOL /* https://developer.mozilla.org/en-US/docs/Tools/Responsive_Design_Mode */
        /* Use tool to easily change page size to see where content breaks */



/*--------------------------------------------------------------------------------------------------------*/
SIZING /* Change the size of an element */
/*--------------------------------------------------------------------------------------------------------*/

    INTRINSIC /* HTLM elements have a natural/intrinsic size, It's dictated by its content */
    
    SPECIFIC /* We can give our content a specific size, Carefull, Doesn't handle overflow well */
    /* Fixing width & height of elements with lengths or percentages needs to be done carefully */
    
    PERCENTAGES /* Percentages act like length units, be aware of what it is a percentage of */
    /* A BOX inside a CONTAINER, Child box width is a percentage of the parent container width */
    /* Percentage Margin/Padding, is calculated on inline width of the element, Strange behaviour possible */

    MIN-MAX /* VERY USEFUL, We can ask CSS to give an element a min or max size */
    /* Very useful for dealing with a variable amount of content, deals with overflow */
    /* Use max-width to scale down images, if not enough space to show at intrinsic size, caps its width */
    /* Can be used to make images responsive, don't load in images that are too big though */
        p { max-width: 100%; } /* Image can shrink, but can't become bigger than its intrinsic width */

    VIEWPORT /* Visible area of your page in the browser you are using to view a site, Units: "vw" "vh" */
    /* Changing the Viewport also changes the size of your box or text, SO BE MINDFUL when using them */
        p { width: 20vw; } /* "vw" unit for viewport width, 1vw is 1% of viewport width */
        p { height: 20vh; } /* "vh" unit for viewport height, 1vh is 1% of viewport height */

    IMG/VID /* IMAGES/VIDEOS are called REPLACED ELEMENTS, we can style those elements as well */
        
        MIN-MAX /* We can give them a min, max size to fit them into our container */
            .img { max-width: 100%; } /* Will fit the image to the container's width */
            .img { min-height: 100%; } /* Will fit the image to the container's height */
        
        OBJECTFIT /* Replaced elements can be sized to fit a box in a variety of ways */
            .img { object-fit: fill; } /* Stretch IMG to fully FILL box, Aspect Ratio NOT respected */
            .img { object-fit: cover; } /* NEATLY fills box, AR maintained, Part of IMG is invisible */
            .img { object-fit: contain; } /* FULL img visible in box, AR NOT maintained */



/*--------------------------------------------------------------------------------------------------------*/
OVERFLOW /* Content overflow happens when there is too much content to fit in the box (container) */
/*--------------------------------------------------------------------------------------------------------*/

/* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/overflow */

    /* CSS focusses on preventing data loss, hence overflowing content even when container is too small */
    .box { overflow: visible; } /* DEFAULT property value, SHOWS overflowing content */    
    .box { overflow: hidden; } /* HIDES overflowing content, ONLY do this if hiding it causes no problem */
    .box { overflow: scroll; } /* Add SCROLLBARS when content overflows, GOOD way of handling overflow */
        .box { overflow-x: scroll; } /* Adds X-HORIZONTAL scrollbar */
        .box { overflow: scroll hidden; } /* Adds X-Horizontal scrollbar, hides the Y-Vertical scrollbar */
        .box { overflow: auto; } /* Automatically detect, scrollbars will be hidden when no overflow */
    /* Modern layout methods manage overflow, they work without assumptions about the amount of content */
    /* When developing a site always test for overflow, small/big text, little/many content */



/*--------------------------------------------------------------------------------------------------------*/
BACKGROUNDS-and-BORDERS /* Style elements background & borders */
/*--------------------------------------------------------------------------------------------------------*/

/* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Backgrounds_and_Borders */

    BACKGROUND
    /* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/background */
    /* Longhands */
        background-color /* Adds color to background of an element. 3 types: RGB, #00000, colorname*/
            p { background-color: red; }
        background-image /* Add image, images, gradients, to the background of an element */
            p { background-image: url(img.png); }
        background-repeat /* Controls tiling behaviour of the background image */
            p { background-repeat: no-repeat; }
        background-size /* Sizes the bkgnd image */
            p { background-size: 10%; }
        background-position /* Uses keywords, length, %, coordinates. Consists: HORIZONTAL, VERTICAL value */
            p { background-position: center; }
        background-attachment /* Affects background behaviour when element has scrollable content */
            p { background-attachment: scroll; }

    /* Shorthands */
    /* RULE: Color can only be specified after the last comma "," */
    /* SIZE may only be included directly after POSITION, sepparated with "/". EX: "center/80%" */
        p { background: no-repeat center/80% url(img.png); } /* Single image, centered, scaled */

    /* Accessibility considerations */
        /* Placing text on top of an img or color, make sure the contract is enough */
        /* Specify a bkgnd color when in case the img doesn't load */
        /* Screen readers don't parse bkgnd images, so make sure vital content is inside the html */


    BORDERS
    /* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/border */
    /* Longhands */
        border-top-width
            p { border-top-width: 0px; }
        border-top-style
            p { border-top-style: solid; }
        border-top-color
            p { border-top-color: red; }

    /* Shorthands */
        p { border: 1px solid black; } /* Set all borders with 1 line */
        p { border-top: 1px solid black; } /* Set top border with 1 line */

        RADIUS
            border-radius    
            p { border-radius: 10px; } /* Set a radius for all border-corners */
            p { border-top-right-radius: 10%, 20%; } /* Set radius only for the top right border-corner */


    SHADOWS
    /* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/box-shadow */
        .box { box-shadow: 2px 2px 2px 1px rgba(0, 0, 0, 0.2); }
            /* X-offset, Y-offset, Blur Radius, Spread Radius, Color */



/*--------------------------------------------------------------------------------------------------------*/
TEXT-STYLING /* Change font, size, align it ... */
/*--------------------------------------------------------------------------------------------------------*/

    COLOR /* Color sets foreground color of selected elements */
        p { color: red; }

/* FONT-STYLES: Font, Size, Weight, ...  */
    SHOTRHAND
    /* ORDER: font-style, font-variant, font-weight, font-stretch, font-size, line-height, font-family */
    /* REQUIRED: font-size & font-family */
    /* FORWARD SLASH: has to be put between font-size and line-height */
        p { font: italic normal bold normal 3em/1.5 Helvetica, Arial, sans-serif; }
    
    FONT-FAMILY /* Changes the font being displayed, if not available displays browsers default font */
    /* https://developer.mozilla.org/en-US/docs/Learn/CSS/Styling_text/Web_fonts - How to use FONTS */
    /* https://www.cssfontstack.com/ - Web Safe Fonts */
        p { font-family: "Trebuchet MS"; }    
        p { font-family: "Trebuchet MS", Verdana, sans-serif; } /* FONT-STACKING, fallback fonts */
        
    FONT-SIZE /* Font size element is inherited from its parent element, Common units: px, em, rem */
    /* Using REM is better than EM, Nesting keeps size stable, with EM sizes change every level */
    /* GOOD idea to cluster you font sizes in a designated area in your stylesheet */
        p { font-size: 10px; } /* Paragraphs text-size is 10px */

    FONT-STYLE /* Turn italic text on/off, Possible rare values: normal, italic, oblique */
        p { font-style: italic; } /* Italic paragraph */
    
    FONT-WEIGHT /* Sets how bold the text is */
        p { font-weight: bold; } /* Bold paragraph */

    FONT-VARIANT /* Switch between small caps and normal font alternatives */
    FONT-VARIANT-POSITION /* Control the usage of superscript or subscript */
    FONT-KERNING /* Switch kerning options on and off */
    FONT-FEATURE-SETTINGS /* Switch various OpenType font features on and off */
    FONT-SIZE-ADJUST /* Adjust the visual size of the font, independently of its actual font size */
    FONT-STRETCH /* Switch between possible alternative stretched versions of a given font */

    GOOGLE-FONT /* Select style -> Embed -> @import -> Implement in css, done */

    WEB-FONT /* When downloading a font, you have to create a WEBFONT from it to use in your site */
    /* DOWNLOAD font, https://www.fontsquirrel.com/ , https://www.dafont.com/ - free */    
    /* LICENCE check, make sure the font is licenced for what you are planning to do with it */
    /* GENERATE web font: https://www.fontsquirrel.com/tools/webfont-generator */
    /* IMPLEMENT, Add @FONT-FACE to the stylesheet for each font, Add all WOFF, WOFF2 files to site */


/* TEXT-LAYOUT-STYLES: Spacing between lines & letters, Alignment of text in box, ... */
    TEXT-ALIGN /* Align: Left, Right, Center, Justify */

    TEXT-DECORATION /* Shorthand, Decorate text: none, underline, overline, line-through */
        p { text-decoration: underline; } /* Underlines the paragraph */
        BORDER-BOTTOM /* Is an alternative, styles a bit different, personal preference /

    TEXT-TRANSFORM /* Transform text: none, uppercase, lowercase, capitalize, full-width */
        p { text-transform: capitalize; } /* Capitalizes the paragraph */
    
    TEXT-SHADOW /* Drop shadow can be applied to text */
    /* https://www.sitepoint.com/moonlighting-css-text-shadow/ */
        p { text-shadow: 4px 4px 5px red; } /* Shadow: Hor.offset, Vert.offset, BlurRadius, Color */
        p { text-shadow: 4px 4px 5px red, 2px 2px 1px red; } /* Multiple shadows can be applied */

    LINE-HEIGHT /* Sets the height of each line of text, Font-Size is multiplied to get the L.H. */
        p { line-height: 1.5; } /* Value between 1.5 and 2 is good. Font-Size multiplied by 1.5 ;  */

    LETTER-SPACING /* Not used often, sets space between letters */
        p { letter-spacing: 4px; }
    WORD-SPACING /* Not used often, sets space between words */
        p { letter-spacing: 4px; }

    TEXT-INDENT /* Specify horizontal space before beginning of first line of text */
    TEXT-OVERFLOW /* Define how overflowed content that is not displayed is signaled to users */
    WHITE-SPACE /* Define how whitespace and associated line breaks insde the element are handled */
    WORD-BREAK /* Specify whether to break lines within words */
    TEXT-ALIGN-LAST /* Define how last line of a block or line, right before forced line break, is aligned */
    TEXT-ORIENTATION /* Define the orientation of the text in a line */
    OVERFLOW-WRAP /* Specify if the browser may break lines within words in order to prevent overflow */
    WRITING-MODE /* Define whether lines run horizontally or vertically and their direction */



/*--------------------------------------------------------------------------------------------------------*/
TEXT-WRITING-MODES /* Text writing direction, left-right, top-bottom, bottom-top, ... */
/*--------------------------------------------------------------------------------------------------------*/

/* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Logical_Properties */
    
    DIRECTION
        h1 { writing-mode: vertical-rl; } /* Right-to-Left block flow, Text runs vertically */
        h1 { writing-mode: horizontal-tb; } /* Top-to-Bottom block flow, Text runs horizontally, default */

    LOGICAL PROPERTIES and VALUES /* Still new, but will be common practice in the furture */
    /* Changing writing mode, brings forth the need for LOGICAL properties & values */
        INLINE-SIZE /* LOGICAL WIDTH, refers to the size in INLINE dimension */
            p { inline-size: 150px; }
        
        BLOCK-SIZE /* LOGICAL HEIGHT, refers to the size in BLOCK dimension */
            p { block-size: 200px; }
            
        PADDING /* LOGICAL padding, corresponds to the "padding-left" property */
            padding-block-start maps padding-top /* PADDING applied to logical START of BLOCK dimension */
            padding-inline-end maps padding-right /* PADDING applied to logical END of INLINE direction */
            padding-block-end maps padding-bottom /* PADDING applied to logical END of BLOCK dimension */
            padding-inline-start maps padding-left /* PADDING applied to logical START of INLINE direction */

        BORDER /* LOGICAL border, corresponds to the "border-bottom" property */
            border-block-start maps border-top /* BORDER applied to logical START of BLOCK dimension */
            border-inline-end maps border-right /* BORDER applied to logical END of INLINE direction */
            border-block-end maps border-bottom /* BORDER applied to logical END of BLOCK dimension */
            border-inline-start maps border-left /* BORDER applied to logical START of INLINE direction */
        
        MARGIN /* LOGICAL margin, corresponds to the "margin-top" property */
            margin-block-start maps margin-top /* MARGIN applied to logical START of BLOCK dimension */
            margin-inline-end maps margin-right /* MARGIN applied to logical END of INLINE direction */
            margin-block-end maps margin-bottom /* MARGIN applied to logical END of BLOCK dimension */
            margin-inline-start maps margin-left /* MARGIN applied to logical START of INLINE direction */



/*--------------------------------------------------------------------------------------------------------*/
FORMS /* Style forms, they are tricky to style */
/*--------------------------------------------------------------------------------------------------------*/

/* INFO: https://developer.mozilla.org/en-US/docs/Learn/Forms */

    /* IMPORTANT: When styling form elements, make sure can still see that they are form elements */
    /* Elements that require TEXT input are easy to style, they behave like other boxes */
    INPUT-STYLING
    input[type="text"], input[type="email"] { border: 2px solid #000; margin: 1px; padding: 10px; }
    input[type="submit"] { border: 3px solid #333; border-radius: 5px; padding: 10px 2em; }

    FORMRESET /* DEFAULT styling differs depending on the OS and BROWSER, hence a reset */
    /* Form elements don't inherit font styling by default in some browsers */
        button, input, select, textarea { font-family : inherit; font-size : 100%; }
    /* Set padding and margin to 0, then add these back in when styling controls */
        button, input, select, textarea { box-sizing: border-box; padding: 0; margin: 0; }
    /* Stop IE showing a scrollbar even when it is not needed */
        textarea { overflow: auto; }



/*--------------------------------------------------------------------------------------------------------*/
LINKS /* <a> Style hyperlinks, states, and icons */
/*--------------------------------------------------------------------------------------------------------*/

/* INFO: https://developer.mozilla.org/en-US/docs/Web/CSS/:link */

    STATES /* Style link states with their pseudo-classes */
    /* The below ORDER is important when styling link states */
        a:link /* Default state */
        a:visited /* State link is in when it's been visited already */
        a:hover /* State when link is hovered over by mouse */
        a:focus /* State when link is focussed, for example by tab navigation */
        a:active /* State if link has been clicked on */
    
    UNDERLINE /* Styling the underline of the link, border-bottom, can also use text-decoration */
        a:hover { border-bottom: 1px solid; background: rgb(70, 81, 143); }

    ICON /* If we want to add an icon to our links we can do this like this */
    a[href*="#"] { background: url('img') no-repeat 100% 0; background-size: 16px 16px; padding-right: 19px; }

    /* This type of styling can also be used for other elements besides links, buttons, lists for example */
    /* https://css-tricks.com/fighting-the-space-between-inline-block-elements/ - Space between buttons *



/*--------------------------------------------------------------------------------------------------------*/
LISTS /* OL Ordered List, UL Unordered List, DL Description List */
/*--------------------------------------------------------------------------------------------------------*/

    LIST-SPACING /* Style to maintain the same vertical rythim and horizontal spacing as other content */
    
        /* Example */
        html { font-family: Helvetica, Arial, sans-serif; font-size: 10px; } /* Set baseline font */
        h2 { font-size: 2rem; } /* Set relative fonts for header */
        ul,ol,dl,p { font-size: 1.5rem; }  /* Set relative fonts list types, children inherit */
        li, p { line-height: 1.5; } /* Sets line spacing for our li items and paragraphs */

    LIST-SPECIFIC-STYLES /* Can be set on <ul> en <ol> elements */

        LIST-STYLE-TYPE /* Sets bullet type, square or circle for UL, number letter or roman for OL */
        LIST-STYLE-POSITION /* Sets whether the bullet appears inside the list items or outside */
        LIST-STYLE-IMAGE /* Use custom image for the bullet, rather than the square or circle */
    
        /* Shorthand, any order, can use 1 or 2 or 3 properties */
        ul { list-style: square url(example.png) inside; }

    /* Advanced Costomization Tools */
        /* https://developer.mozilla.org/en-US/docs/Web/CSS/@counter-style */
        /* https://developer.mozilla.org/en-US/docs/Web/CSS/counter-increment */
        /* https://developer.mozilla.org/en-US/docs/Web/CSS/counter-reset */



/*--------------------------------------------------------------------------------------------------------*/
TABLES /* Not the most glamorous job in world, but sometimes it has to be done */
/*--------------------------------------------------------------------------------------------------------*/

/* https://css-tricks.com/fixing-tables-long-strings/ - Fixing table layout */

    TABLE-STYLING
        /* Size columns to the width of their headings, then style further from there */
        table { table-layout: fixed; } /* Best practice, table behave more predictable by default */
        /* Table width 100% makes our table responsive, Needs more work to look ok on narrow screen sizes */
        table { width: 100%; } /* Table will fit in any container it is put in */
        /* We should collapse our table borders, BEST PRACTICE, by default it doesn't look good */
        table { border-collapse: collapse; }
        /* Set a table border around the whole table for visability purposes */
        table { border: 3px solid purple; }
        /* Give our <th> <td> some space to breathe */
        th, td { padding: 20px; }
        /* Set individual column width for each column */
        thead th:nth-child(1) { width: 30%; } /* Select the 1-th child, that is a <th>, inside a <thead> */
        thead th:nth-child(n) { width: 20%; } /* Select the n-th child, that is a <th>, inside a <thead> */

    TYPOGRAPHY /* We can find font sheets on https://fonts.google.com/ to LINK to in our <header> */
        html { font-family: 'helvetica neue', helvetica, arial, sans-serif; }
        thead th, tfoot th { font-family: 'Rock Salt', cursive; }
        th { letter-spacing: 2px; }
        td { letter-spacing: 1px; }
        tbody td { text-align: center; }
        tfoot th { text-align: right; }

    GRAPHICS and COLORS
    /* Style the thead and tfoot */    
        thead, tfoot { background: url(img.jpg); color: white; text-shadow: 1px 1px 1px black; }
        thead th, tfoot th, tfoot td { background-color: #000; border: 3px solid purple; }
    /* ROW COLOR SWAP */
        tbody tr:nth-child(odd) { background-color: #ff33cc; }
        tbody tr:nth-child(even) { background-color: #e495e4; }              
        tbody tr { background-image: url(noise.png); }
        table { background-color: #ff33cc; }
    /* Style the caption */
        caption { font-family: 'Rock Salt', cursive; padding: 20px; font-style: italic; caption-side: bottom;
                color: #666; text-align: right; letter-spacing: 1px; }



/*--------------------------------------------------------------------------------------------------------*/
DEBUGGING /* Using the Dev Tools to debug CSS */
/*--------------------------------------------------------------------------------------------------------*/

/* INFO: https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_are_browser_developer_tools */
/* INSPECT, CMD+SHIFT+C, We can inspect an element, HTML CSS */
    
    CSS RULE VIEWER
    /* INSPECT CSS rules, Directly applied, Inheritted */
    /* EXPAND shorthand declarations, click the ARROW in front of the value */
    /* TOGGLE rules ON and OFF and see change instantly, click the RADIO button */
    /* EDIT VALUES in the browser, click the value */
    /* ADD PROPERTIES in the browser, click CURLY BRACE to add a new rule */
    
    LAYOUT VIEWER
    /* VISUAL representation of the BOX MODEL */
    /* INSPECT values, even if we didn't define them, some still influence the design */
    /* EDIT values visually on the box */

    SPECIFICITY ISSUES
    /* INSPECT elements and see what css rule is applied and which one is crossed */

    DEBUGGING STEPS
    /* TAKE A STEP BACK! When frustration builds, go for a walk-talk-work on something else first */
    /* VALIDATE YOUR CODE */
        /* CSS:   https://jigsaw.w3.org/css-validator/ */
        /* HTML:  https://validator.w3.org/ */
    /* PROPERTY & VALUE supported by test browser? If browser doesn't understand, it ignores the rule */
    /* SPECIFICITY, Is some rule overwriting your CSS, use DEV TOOL to see easily */
    /* REDUCE TEST CASE, create a reduced version of the problem, Step by step */
        /* Isolate the HTML and styling, remove JS */
    
    /* NOT FIXED? If all this doesn't help, post reduced test case to a forum */



/*--------------------------------------------------------------------------------------------------------*/
USEFUL LINKS /* NEEDS REWORK!!!!!! */
/*--------------------------------------------------------------------------------------------------------*/


/* MDN CSSDOCS https://developer.mozilla.org/en-US/docs/Web/CSS */
/* CSS REFERENCES https://developer.mozilla.org/en-US/docs/Web/CSS/Reference */

SHORTHANDS
/* SHORTHANDS: https://developer.mozilla.org/en-US/docs/Web/CSS/Shorthand_properties */

SELECTORS
/* PSEUDO CLASSES https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes */
/* PSEUDO ELEMENTS https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements */

BOX-STYLING
    BACKGROUND AND BORDERS
    /* https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Backgrounds_and_Borders */

LAYOUT
    COOKBOOK
    /* https://developer.mozilla.org/en-US/docs/Web/CSS/Layout_cookbook */
    LOGICAL PROPERTIES
    /* https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Logical_Properties */
    LEGACY
    /* https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Legacy_Layout_Methods */

TEXT-STYLING
    FONT-STYLING
    /* HOW TO FONTS https://developer.mozilla.org/en-US/docs/Learn/CSS/Styling_text/Web_fonts */
    /* WEB SAFE FONTS https://www.cssfontstack.com/ */
    /* GOOGLE FONTS https://fonts.google.com/ */
    /* FREE https://www.fontsquirrel.com/ , https://www.dafont.com/ , https://everythingfonts.com/ */
    /* WEB FONT GENERATOR https://www.fontsquirrel.com/tools/webfont-generator */
    /* VARIBALE FONTS https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Fonts/Variable_Fonts_Guide */
    TEXT-STYLING
    /* SHADOW: https://www.sitepoint.com/moonlighting-css-text-shadow/ */
    WRITING MODES
    /* LOGICAL PROP https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Logical_Properties */

GLOBAL-STYLING
    COLORS
    /* https://developer.mozilla.org/en-US/docs/Web/CSS/color_value */
    IMAGES
    /* https://developer.mozilla.org/en-US/docs/Web/CSS/image */
    FORMS
    /* https://developer.mozilla.org/en-US/docs/Learn/Forms */
    TABLES
    /* https://css-tricks.com/fixing-tables-long-strings/ - Fix table layout */
    VARIABLES    
    /* https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties */

DEBUGGING
/* DEV TOOL https://developer.mozilla.org/en-US/docs/Tools */
/* HOW TOS https://developer.mozilla.org/en-US/docs/Tools/Page_Inspector#How_to */


/*--------------------------------------------------------------------------------------------------------*/  
TESTER /* Code tester */
/*--------------------------------------------------------------------------------------------------------*/

a { 
    background-size: 100%;
    list-style-type: lower-latin;
 }

/*--------------------------------------------------------------------------------------------------------*/
/*--------------------------------------------------------------------------------------------------------*/
