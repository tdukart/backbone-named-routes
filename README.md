# Add named routes to your Backbone application.

## Usage

Include the plugin after all dependencies.

    <script src="/javascripts/underscore.js type="text/javascript"></script>
    <script src="/javascripts/json2.js type="text/javascript"></script>
    <script src="/javascripts/jquery.js type="text/javascript"></script>
    <script src="/javascripts/backbone.js type="text/javascript"></script>
    <script src="/javascripts/backbone_named_routes.js type="text/javascript"></script>

Given a Backbone Router:

    var routes = {
      "help":                 "help",    // #help
      "search/:query":        "search",  // #search/kiwis
      "search/:query/p:page": "search"   // #search/kiwis/p7
    };
      
    Backbone.NamedRoutes.addRoutes(routes);

    var Workspace = Backbone.Router.extend({
      routes: routes
    });


This plugin provides a new property of the `Backbone` global that provides named routes
which can be accessed through

    Backbone.NamedRoutes.helpPath()
    => "help"
    
    Backbone.NamedRoutes.search('kiwis')
    => "search/kiwis"
    
    Backbone.NamedRoutes.search('kiwis', 7)
    => "search/kiwis/p7"

## Query parameters

Named routes accept an optional parameter that will append query parameters to the path.

    var router = new Workspace();

    router.helper.helpPath({ foo: "bar", baz: "boo" });
    => "/help?foo=bar&baz=boo"

    router.helper.searchPath("kiwis", { foo: "bar", baz: "boo" });
    => "/search/kiwis?foo=bar&baz=boo"

    router.helper.searchPath("kiwis", 7, { foo: "bar", baz: "boo" });
    => "/search/kiwis/p7?foo=bar&baz=boo"
