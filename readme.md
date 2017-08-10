For this i have used the css examples from Minton
source: https://wrapbootstrap.com/theme/minton-admin-frontend-rtl-php-mvc5-WB0858DB6

To dynamically change the CSS files i changed the structure a little bit.

File structure
<pre>
css
    assetsBlue
        bootstrap.min.css
        icons.css
        components.css
        pages.css
        menu.css
        responsive.css
        core.css
    assetsDark
        bootstrap.min.css
        icons.css
        components.css
        pages.css
        menu.css
        responsive.css
        core.css
    assetsGreen
        bootstrap.min.css
        icons.css
        components.css
        pages.css
        menu.css
        responsive.css
        core.css
    assetsPurple
        bootstrap.min.css
        icons.css
        components.css
        pages.css
        menu.css
        responsive.css
        core.css
    assetsYellow
        bootstrap.min.css
        icons.css
        components.css
        pages.css
        menu.css
        responsive.css
        core.css
</pre>
    
The javascript functions
    
 <pre>   
function switch_css_scheme(whatColor) {
    "use strict";
    var cssNode = {};
    var headID = {};
    // the css files 
    var css_array = new Array(
        'bootstrap.min.css',
        'icons.css',
        'components.css',
        'pages.css',
        'menu.css',
        'responsive.css',
        'core.css');
    for(var a=0; a< css_array.length; a++){
        remove_css_scheme(css_array[a]);
        cssNode = document.createElement('link');
        cssNode.type = 'text/css';
        cssNode.rel = 'stylesheet';
        cssNode.media = 'screen';
        headID = document.getElementsByTagName("head")[0];
        cssNode.href = '../css/assets' + whatColor + '/'+css_array[a];
        headID.appendChild(cssNode);
    }
}

    
function remove_css_scheme(filename) {
    "use strict";
    var targetElement = "link";
    var targetAttr = "href";
   var allCtrl = document.getElementsByTagName(targetElement);
    for (var i = allCtrl.length-1; i >= 0; i--) { //search backwards within nodelist for matching elements to remove
        if (allCtrl[i] && allCtrl[i].getAttribute(targetAttr) != null && allCtrl[i].getAttribute(targetAttr).indexOf(filename) != -1) {
            allCtrl[i].parentNode.removeChild(allCtrl[i]);
        }
    }
}    

</pre>
Sample call for testing

<pre>
< button class="btn btn-primary waves-effect waves-light btn-xs m-b-5" onclick="javascript:switch_css_scheme('Dark')">Dark</button>
< button class="btn btn-primary waves-effect waves-light btn-xs m-b-5" onclick="javascript:switch_css_scheme('Blue')">Blue</button>
< button class="btn btn-primary waves-effect waves-light btn-xs m-b-5" onclick="javascript:switch_css_scheme('Yellow')">Yellow</button>
< button class="btn btn-primary waves-effect waves-light btn-xs m-b-5" onclick="javascript:switch_css_scheme('Green')">Green</button>
< button class="btn btn-primary waves-effect waves-light btn-xs m-b-5" onclick="javascript:switch_css_scheme('Purple')">Purple</button>
 ^ remove this space
</pre>
