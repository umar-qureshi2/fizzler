# fizzler
Automatically exported from code.google.com/p/fizzler
A .NET library to select items from a node tree based on a CSS selector. The default implementation is based on HTMLAgilityPack and selects from HTML documents. There over 140 unit tests - see below for more information. The tests are based on the jQuery selector engine tests.

Fizzler supports .NET 2.0, 3.0, 3.5 and Mono.

Contributions are welcome in forms of:

Increased selector support
Implementation over an HTML-like hierarchical document model
Re-factorings
Improved tests
Examples
// Load the document using HTMLAgilityPack as normal
var html = new HtmlDocument();
html.LoadHtml(@"
  <html>
      <head></head>
      <body>
        <div>
          <p class='content'>Fizzler</p>
          <p>CSS Selector Engine</p></div>
      </body>
  </html>");

// Fizzler for HtmlAgilityPack is implemented as the 
// QuerySelectorAll extension method on HtmlNode

var document = html.DocumentNode;

// yields: [<p class="content">Fizzler</p>]
document.QuerySelectorAll(".content"); 

// yields: [<p class="content">Fizzler</p>,<p>CSS Selector Engine</p>]
document.QuerySelectorAll("p");

// yields empty sequence
document.QuerySelectorAll("body>p");

// yields [<p class="content">Fizzler</p>,<p>CSS Selector Engine</p>]
document.QuerySelectorAll("body p");

// yields [<p class="content">Fizzler</p>]
document.QuerySelectorAll("p:first-child");
