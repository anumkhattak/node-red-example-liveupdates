Load this into Node-Red:

```
[{"id":"59f72869.760188","type":"subflow","name":"Master Page Template","in":[{"x":85,"y":152,"wires":[{"id":"ec121b2b.503b5"}]}],"out":[]},{"id":"a8053ede.4604d","type":"template","name":"Master Page Template","field":"payload","format":"handlebars","template":"<!DOCTYPE html> \n<html>\n<head>\n\t<title>{{payload.pgTitle}}</title>\n\t<meta name=\"viewport\" content=\"width=device-width, initial-scale=1\">\n\t<meta charset=\"utf-8\">\n\t<meta http-equiv=\"X-UA-Compatible\" content=\"IE=edge\" />\n\t<link href=\"https://cdnjs.cloudflare.com/ajax/libs/foundation/5.5.1/css/normalize.min.css\" rel=\"stylsheet\">\n\t<link href=\"https://cdnjs.cloudflare.com/ajax/libs/foundation/5.5.1/css/foundation.min.css\" rel=\"stylesheet\">\n\t<link href=\"https://cdnjs.cloudflare.com/ajax/libs/foundicons/3.0.0/foundation-icons.css\" rel=\"stylesheet\">\n\t{{! Supports old browsers AND detects mobile browsers: install via Bower }}\n\t<script src=\"/bower_components/modernizer/modernizr.js\"></script>\n</head>\n\n<body>\n    <div class=\"contain-to-grid sticky\"><nav class=\"top-bar\" data-topbar role=\"navigation\" data-options=\"sticky_on: [medium,large]\">\n        <ul class=\"title-area\">\n            <li class=\"name\">\n                <h1><a href=\"/\">{{payload.pgTitle}}</a></h1>\n            </li>\n            <!-- Remove the class \"menu-icon\" to get rid of menu icon. Take out \"Menu\" to just have icon alone -->\n            <li class=\"toggle-topbar menu-icon\"><a href=\"#\"><span>Menu</span></a></li>\n        </ul>\n        <section class=\"top-bar-section\">\n            <ul class=\"right\">\n                <li class=\"divider\"></li>\n                <li class=\"has-dropdown\">\n                    <a href=\"#\">Sensors</a>\n                    <ul class=\"dropdown\">\n                        <li><a href=\"/hall\">Hall</a></li>\n                        <li><a href=\"/loft\">Loft</a></li>\n                        <li><a href=\"/pir\">PIR</a></li>\n                        <li><a href=\"/latest\">Latest Sensor Readings</a></li>\n                        <li><a href=\"/details\">Sensor Details</a></li>\n                    </ul>\n                </li>\n                <li class=\"has-dropdown\">\n                    <a href=\"#\">Weather</a>\n                    <ul class=\"dropdown\">\n                        <li><a href=\"/weather\">Forecasts</a></li>\n                        <li><a href=\"/wCurrent\">Current Conditions</a></li>\n                        <li class=\"has-dropdown\">\n                            <a href=\"#\">WU Raw</a>\n                            <ul class=\"dropdown\">\n                                <li><a href=\"http://api.wunderground.com/api/5cc2ade61d20a937/geolookup/q/UK/Sheffield.json\">Sheffield Stations</a></li>\n                                <li><a href=\"http://www.wunderground.com/personal-weather-station/dashboard?ID=ISHEFFIE15\">Lodgemoor Dashboard</a></li>\n                                <li><a href=\"http://api.wunderground.com/api/5cc2ade61d20a937/conditions/q/pws:ISHEFFIE15.json\">Current Conditions: Lodgemoor: JSON</a></li>\n                                <li><a href=\"http://api.wunderground.com/api/5cc2ade61d20a937/conditions/q/pws:ISHEFFIE22.json\">Current Conditions: Endcliffe Vale Road: JSON</a></li>\n                                <li><a href=\"http://api.wunderground.com/api/5cc2ade61d20a937/conditions/q/pws:ISHEFFIE8.json\">Current Conditions: Endcliffe Corner: JSON</a></li>\n                            </ul>\n                        </li>\n                    </ul>\n                </li>\n                <li class=\"has-dropdown\">\n                    <a href=\"#\">Misc</a>\n                    <ul class=\"dropdown\">\n                        <li><a href=\"/\">Home page</a></li>\n                        <li><a href=\"http://{{global.nrSrv}}:6680/\">Audio Player (Mopidy)</a></li>\n                        <li><a href=\"/red\">Admin interface</a></li>\n                        <li><a href=\"/places\">Places (location information)</a></li>\n                        <li class=\"divider\"></li>\n                        <li><a href=\"jqmobile\">Test Mobile Page</a></li>\n                        <li><a href=\"/freeboard/#start-85157\">Freeboard Test</a></li>\n                        <li class=\"has-dropdown\">\n                            <a href=\"#\">Vis</a>\n                            <ul class=\"dropdown\">\n                                <li><a href=\"/vis/index.html#DemoView\">DemoView</a></li>\n                                <li><a href=\"/vis/edit.html#DemoView\">DemoView (Edit)</a></li>\n                            </ul>\n                        </li>\n                    </ul>\n                </li>\n                <li class=\"has-dropdown\">\n                    <a href=\"#\">Docs</a>\n                    <ul class=\"dropdown\">\n                        <li><a href=\"http://nodered.org/docs/\" target=\"_blank\" title=\"New Window\">Node-Red</a></li>\n                        <li><a href=\"http://mustache.github.io/mustache.5.html\" target=\"_blank\" title=\"New Window\">Mustache</a></li>\n                        <li><a href=\"https://nodejs.org/docs/v0.10.0/api/\" target=\"_blank\" title=\"New Window\">Node v10 API</a></li>\n                        <li><a href=\"http://foundation.zurb.com/docs/\" target=\"_blank\" title=\"New Window\">Zurb Foundation</a></li>\n                        <li><a href=\"https://princessdesign.net/foundation-cheat-sheet/\" target=\"_blank\" title=\"New Window\">Foundation Cheat Sheet</a></li>\n                        <li class=\"divider\"></li>\n                        <li><a href=\"http://flows.nodered.org/\" target=\"_blank\" title=\"New Window\">NR Node Library</a></li>\n                        <li><a href=\"http://red-nodes.org/\" target=\"_blank\" title=\"New Window\">NR Nodes on NPM (red.nodes)</a></li>\n                        <li><a href=\"http://cnpmjs.org/browse/keyword/node-red\" target=\"_blank\" title=\"New Window\">NR Nodes on NPM (CNPM)</a></li>\n                        <li class=\"divider\"></li>\n                        <li><a href=\"https://github.com/node-red/node-red-nodes/wiki/Node-Ideas\" target=\"_blank\" title=\"New Window\">NR Node Ideas (NR WIKI)</a></li>\n                    </ul>\n                </li>\n                \n        </ul></section>\n    </nav></div>\n    {{! Main content - HTML must be in msg.payload.content }}\n    <section role=\"main\" class=\"scroll-container\"><div class=\"row\">\n        {{{payload.content}}}\n    </div></section>\n    <script src=\"https://cdnjs.cloudflare.com/ajax/libs/jquery/2.1.3/jquery.min.js\"></script>\n    {{! rws auto reconnects websockets: install via bower }}\n    <script src=\"/bower_components/reconnectingWebsocket/reconnecting-websocket.min.js\"></script>\n    {{! foundation.min.js loads ALL plugins }}\n    <script src=\"https://cdnjs.cloudflare.com/ajax/libs/foundation/5.5.1/js/foundation.min.js\"></script>\n    {{! Load mqtt.js to get MQTT over web services - TODO: make this optional & pass addr of mqtt server }}\n    {{! @see http://git.eclipse.org/c/paho/org.eclipse.paho.mqtt.javascript.git/plain/src/mqttws31.js }}\n    <script src=\"/js/mqttws31.js\"></script>\n    {{! Load any additional scripts if reqd, including inline code - the activation code for optional ws support should be in this }}\n    {{{payload.script1}}}\n    {{! Load my standard code for all pages, see ./public/ }}\n    <script src=\"/js/ws.js\"></script>\n</body>\n</html>","x":462.1666564941406,"y":152.1666717529297,"z":"59f72869.760188","wires":[["4421c323.72baa4"]]},{"id":"3cd8a2a6.be6bce","type":"comment","name":"Defines a common page layout to be used for all pages","info":"The following entities are expected on the msg.payload object:\n\n- pageTitle [Used in the head/title & menu]\n- menu [creates the menu]\n- content [must be HTML formatted output]\n- script1 [HTML formatted - usually a scirpt block]","x":364.1666717529297,"y":101.16667175292969,"z":"59f72869.760188","wires":[]},{"id":"4421c323.72baa4","type":"http response","name":"","x":641.1666259765625,"y":152.16665649414062,"z":"59f72869.760188","wires":[]},{"id":"b9728f9e.242658","type":"e-mail","server":"smtp.gmail.com","port":"465","name":"j.knightnet@gmail.com","dname":"To Gmail","x":648.88330078125,"y":239.88333129882812,"z":"59f72869.760188","wires":[]},{"id":"78413c13.b6044c","type":"comment","name":"This works except for JS so no charts","info":"","x":643.88330078125,"y":204.88333129882812,"z":"59f72869.760188","wires":[]},{"id":"ec121b2b.503b5","type":"function","name":"Cp globals to payload","func":"msg.payload.global = {\n    'mqttSrv'       : context.globalmqttSrv,\n    'mqttWsPort'    : context.globalmqttWsPort,\n    'nrSrv'         : context.globalnrSrv,\n    'nrPort'        : context.globalnrPort,\n    'wanMqttSrv'    : context.globalwanMqttSrv,\n    'wanMqttWsPort' : context.globalwanMqttWsPort,\n    'wanNrSrv'      : context.globalwanNrSrv,\n    'wanNrPort'     : context.globalwanNrPort\n};\n\nreturn msg;","outputs":1,"valid":true,"x":232.88333129882812,"y":151.88333129882812,"z":"59f72869.760188","wires":[["a8053ede.4604d"]]},{"id":"54efd496.35537c","type":"http in","name":"","url":"/input","method":"get","x":79.5,"y":1360,"z":"7f7e9fdc.66f4e8","wires":[["ae2e3250.e91b2","951539ee.d29bb8"]]},{"id":"72fe6d21.9f1e8c","type":"template","name":"Input Form","field":"payload.content","format":"handlebars","template":"<form id=\"myform\">\n\t<div class=\"row\">\n\t\t<div class=\"large-12 columns\">\n\t\t\t<label>Input Label\n\t\t\t\t<input type=\"text\" placeholder=\"large-12.columns\" />\n\t\t\t</label>\n\t\t</div>\n\t</div>\n\t<div class=\"row\">\n\t\t<div class=\"large-4 columns\">\n\t\t\t<label>Input Label\n\t\t\t\t<input type=\"text\" placeholder=\"large-4.columns\" />\n\t\t\t</label>\n\t\t</div>\n\t\t<div class=\"large-4 columns\">\n\t\t\t<label>Input Label\n\t\t\t\t<input type=\"text\" placeholder=\"large-4.columns\" />\n\t\t\t</label>\n\t\t</div>\n\t\t<div class=\"large-4 columns\">\n\t\t\t<div class=\"row collapse\">\n\t\t\t\t<label>Input Label</label>\n\t\t\t\t<div class=\"small-9 columns\">\n\t\t\t\t\t<input type=\"text\" placeholder=\"small-9.columns\" />\n\t\t\t\t</div>\n\t\t\t\t<div class=\"small-3 columns\">\n\t\t\t\t\t<span class=\"postfix\">.com</span>\n\t\t\t\t</div>\n\t\t\t</div>\n\t\t</div>\n\t</div>\n\t<fieldset>\n\t\t<legend>Fieldset Legend</legend>\n\t\t<div class=\"row\">\n\t\t\t<div class=\"large-12 columns\">\n\t\t\t\t<label>Select Box\n\t\t\t\t\t<select id=\"selectbox\">\n\t\t\t\t\t\t<option value=\"husker\">Husker</option>\n\t\t\t\t\t\t<option value=\"starbuck\">Starbuck</option>\n\t\t\t\t\t\t<option value=\"hotdog\">Hot Dog</option>\n\t\t\t\t\t\t<option value=\"apollo\">Apollo</option>\n\t\t\t\t\t</select>\n\t\t\t\t</label>\n\t\t\t</div>\n\t\t</div>\n\t\t<div class=\"row\">\n\t\t\t<div class=\"large-6 columns\">\n\t\t\t\t<label>Choose Your Favorite</label>\n\t\t\t\t<input type=\"radio\" name=\"pokemon\" value=\"Red\" id=\"pokemonRed\"><label for=\"pokemonRed\">Red</label>\n\t\t\t\t<input type=\"radio\" name=\"pokemon\" value=\"Blue\" id=\"pokemonBlue\"><label for=\"pokemonBlue\">Blue</label>\n\t\t\t</div>\n\t\t\t<div class=\"large-6 columns\">\n\t\t\t\t<label>Check these out</label>\n\t\t\t\t<input id=\"checkbox1\" type=\"checkbox\"><label for=\"checkbox1\">Checkbox 1</label>\n\t\t\t\t<input id=\"checkbox2\" type=\"checkbox\"><label for=\"checkbox2\">Checkbox 2</label>\n\t\t\t</div>\n\t\t</div>\n\t</fieldset>\n\t<div class=\"row\">\n\t\t<div class=\"large-12 columns\">\n\t\t\t<label>Textarea Label\n\t\t\t\t<textarea id=\"textbox\" placeholder=\"small-12.columns\"></textarea>\n\t\t\t</label>\n\t\t</div>\n\t</div>\n\n\t<hr>\n\t<!-- Switch tests -->\n\t<div class=\"row\">\n\t\t<div class=\"switch small-2 columns\">\n\t\t\t<input id=\"exampleCheckboxSwitch\" type=\"checkbox\">\n\t\t\t<label for=\"exampleCheckboxSwitch\"></label>\n\t\t</div> \n\n\t\t<!-- Using radio buttons – each switch turns off the other two -->\n\t\t<div class=\"switch small small-2 columns\">\n\t\t\t<input id=\"exampleRadioSwitch1\" type=\"radio\" checked name=\"testGroup\">\n\t\t\t<label for=\"exampleRadioSwitch1\"></label>\n\t\t</div> \n\n\t\t<div class=\"switch radius small-2 columns\">\n\t\t\t<input id=\"exampleRadioSwitch2\" type=\"radio\" name=\"testGroup\">\n\t\t\t<label for=\"exampleRadioSwitch2\"></label>\n\t\t</div> \n\n\t\t<div class=\"switch round large small-2 columns\">\n\t\t\t<input id=\"exampleRadioSwitch3\" type=\"radio\" name=\"testGroup\">\n\t\t\t<label for=\"exampleRadioSwitch3\"></label>\n\t\t</div>\n\t</div>\n\n\t<hr>\n\t<!-- Complex input boxes -->\n\t<div class=\"row collapse\">\n\t\t<div class=\"small-3 large-2 columns\">\n\t\t\t<span class=\"prefix\">http://</span>\n\t\t</div>\n\t\t<div class=\"small-9 large-10 columns\">\n\t\t\t<input id=\"url\" type=\"text\" placeholder=\"Enter your URL...\">\n\t\t</div>\n\t</div>\n\t<div class=\"row\">\n\t\t<div class=\"large-12 columns\">\n\t\t\t<div class=\"row collapse\">\n\t\t\t\t<div class=\"small-10 columns\">\n\t\t\t\t\t<input type=\"text\" placeholder=\"Hex Value\" aria-describedby=\"nameHelpText\">\n\t\t\t\t</div>\n\t\t\t\t<div class=\"small-2 columns\">\n\t\t\t\t\t<a href=\"#\" id =\"btnGo1\" class=\"button postfix\">Go</a>\n\t\t\t\t</div>\n\t\t\t\t<!-- Help text for an input box (accessible) -->\n\t\t\t\t<p id=\"nameHelpText\">Enter your name.</p>\n\t\t\t</div>\n\t\t</div>\n\t</div>\n\t<div class=\"row\">\n\t\t<div class=\"large-6 columns\">\n\t\t\t<div class=\"row collapse prefix-radius\">\n\t\t\t\t<div class=\"small-3 columns\">\n\t\t\t\t\t<span class=\"prefix\">Label</span>\n\t\t\t\t</div>\n\t\t\t\t<div class=\"small-9 columns\">\n\t\t\t\t\t<input type=\"text\" placeholder=\"Value\">\n\t\t\t\t</div>\n\t\t\t</div>\n\t\t</div>\n\t\t<div class=\"large-6 columns\">\n\t\t\t<div class=\"row collapse postfix-radius\">\n\t\t\t\t<div class=\"small-9 columns\">\n\t\t\t\t\t<input type=\"text\" placeholder=\"Value\">\n\t\t\t\t</div>\n\t\t\t\t<div class=\"small-3 columns\">\n\t\t\t\t\t<span class=\"postfix\">Label</span>\n\t\t\t\t</div>\n\t\t\t</div>\n\t\t</div>\n\t</div>\n\t<div class=\"row\">\n\t\t<div class=\"large-6 columns\">\n\t\t\t<div class=\"row collapse prefix-round\">\n\t\t\t\t<div class=\"small-3 columns\">\n\t\t\t\t\t<a href=\"#\" class=\"button prefix\">Go</a>\n\t\t\t\t</div>\n\t\t\t\t<div class=\"small-9 columns\">\n\t\t\t\t\t<input type=\"text\" placeholder=\"Value\">\n\t\t\t\t</div>\n\t\t\t</div>\n\t\t</div>\n\t\t<div class=\"large-6 columns\">\n\t\t\t<div class=\"row collapse postfix-round\">\n\t\t\t\t<div class=\"small-9 columns\">\n\t\t\t\t\t<input type=\"text\" placeholder=\"Value\">\n\t\t\t\t</div>\n\t\t\t\t<div class=\"small-3 columns\">\n\t\t\t\t\t<a href=\"#\" class=\"button postfix\">Go</a>\n\t\t\t\t</div>\n\t\t\t</div>\n\t\t</div>\n\t</div>\n\n\t<hr>\n\t<!-- Slider http://foundation.zurb.com/docs/components/range_slider.html -->\n\t<!-- Full inderaction requires <script src=\"js/foundation/foundation.slider.js\"></script> & $(document).foundation();  -->\n\t<div class=\"row\">\n\t\t<div class=\"small-7 columns\">\n\t\t\t<label id=\"ageLabel\">Age</label>\n\t\t\t<div id=\"ageHelpText\">How old are you?</div>\n\t\t\t<div id=\"sliderOutput3\"></div>\n\t\t\t<!-- Other data-options: step, start, end -->\n\t\t\t<div id=\"slider1\" class=\"range-slider\" data-slider data-options=\"display_selector: #sliderOutput3;\">\n\t\t\t\t<span class=\"range-slider-handle\" role=\"slider\" aria-labelledby=\"ageLabel\" aria-describedby=\"ageHelpText\"></span>\n\t\t\t\t<span class=\"range-slider-active-segment\"></span>\n\t\t\t\t<!-- NOT ACTUALLY NEEDED? -->\n\t\t\t\t<input id=\"sliderInput3\" type=\"hidden\">\n\t\t\t</div>\n\t\t</div>\n\t</div>\n\t<div class=\"row\">\n\t\t<!-- Vertical with rounded slider -->\n\t\t<div class=\"small-1 columns\" id=\"sliderOutput4\"></div>\n\t\t<div class=\"small-11 columns\">\n\t\t\t<div id=\"slider2\" name=\"nameslider2\" class=\"range-slider vertical-range round\" data-slider data-options=\"vertical: true; display_selector: #sliderOutput4;\">\n\t\t\t\t<!-- Note use of aria-label here because there is no actual label -->\n\t\t\t\t<span class=\"range-slider-handle\" role=\"slider\" tabindex=\"0\" aria-label=\"Age\"></span>\n\t\t\t\t<span class=\"range-slider-active-segment\"></span>\n\t\t\t\t<!-- NOT ACTUALLY NEEDED? -->\n\t\t\t\t<input type=\"hidden\">\n\t\t\t</div>\n\t\t</div>\n\t</div>\n\n\t<hr>\n\t<!-- Buttons -->\n\t<div class=\"row\">\n\t\t<h1>Buttons</h1>\n\t\t<h2>Foundation (&lt;a&gt;)</h2>\n\t\t<!-- Size Classes -->\n\t\t<a href=\"#\" class=\"button tiny\">Tiny Button</a>\n\t\t<a href=\"#\" class=\"button small\">Small Button</a>\n\t\t<a href=\"#\" class=\"button\">Default Button</a>\n\t\t<a href=\"#\" class=\"button disabled\">Disabled Button</a>\n\t\t<a href=\"#\" class=\"button large\">Large Button</a>\n\t\t<a href=\"#\" class=\"button expand\">Expanded Button</a>\n\t\t<!-- Radius Classes -->\n\t\t<a href=\"#\" class=\"button round\">Round Button</a>\n\t\t<a href=\"#\" class=\"button radius\">Radius Button</a>\n\t</div>\n\t<div class=\"row\">\n\t\t<!-- Group: can also use classes even-2 to even-8 to make that number of buttons expand to full width -->\n\t\t<!--        stack and stack-for-small classes make vertical groups -->\n\t\t<!--        button-bar is a class for grouping button groups -->\n\t\t<ul class=\"button-group round\">\n\t\t\t<!-- Color Classes -->\n\t\t\t<li><a href=\"#\" class=\"button\">Default Button</a></li>\n\t\t\t<li><a href=\"#\" class=\"button success\">Success Button</a></li>\n\t\t\t<li><a href=\"#\" class=\"button secondary\">Secondary Button</a></li>\n\t\t\t<li><a href=\"#\" class=\"button alert\">Alert Button</a></li>\n\t\t\t<li><a href=\"#\" class=\"button info\">Info Button</a></li>\n\t\t\t<li><a href=\"#\" class=\"button disabled\">Disabled Button</a></li>\n\t\t</ul>\n\t</div>\n\t<div class=\"row\">\n\t\t<h2>Foundation Split (&lt;a&gt;)</h2>\n\t\t<!-- Split (dropdown) buttons -->\n\t\t<a href=\"#\" class=\"button split\">Split Button <span data-dropdown=\"drop1\"></span></a><br>\n\t\t<ul id=\"drop1\" class=\"f-dropdown\" data-dropdown-content>\n\t\t\t<li><a href=\"#\">This is a link</a></li>\n\t\t\t<li><a href=\"#\">This is another</a></li>\n\t\t\t<li><a href=\"#\">Yet another</a></li>\n\t\t</ul>\n\n\t\t<!-- class=\"[tiny small medium large] [secondary alert success] [radius round] button split\" -->\n\t\t<a href=\"#\" class=\"small success button split\">Small Success Split Button <span data-dropdown=\"drop2\"></span></a><br>\n\t\t<ul id=\"drop2\" class=\"f-dropdown\" data-dropdown-content>\n\t\t\t<li><a href=\"#\">This is a link</a></li>\n\t\t\t<li><a href=\"#\">This is another</a></li>\n\t\t\t<li><a href=\"#\">Yet another</a></li>\n\t\t</ul>\n\n\t\t<!-- Custom pip -->\n\t\t<a href=\"#\" class=\"button split no-pip\">Custom Pip<span><i class=\"fi-arrow-down\"></i></span></a>\n\t\t<ul id=\"drop3\" class=\"f-dropdown\" data-dropdown-content>\n\t\t\t<li><a href=\"#\">This is a link</a></li>\n\t\t\t<li><a href=\"#\">This is another</a></li>\n\t\t\t<li><a href=\"#\">Yet another</a></li>\n\t\t</ul>\n\n\t</div>\n\t<!-- dropdowns and split buttons use the same dropdown addin -->\n\t<!-- http://foundation.zurb.com/docs/components/dropdown.html -->\n\t<div class=\"row\">\n\t\t<a href=\"#\" data-options=\"align:left\" data-dropdown=\"drop4\" class=\"button\">Link Dropdown &raquo;</a>\n\t\t<!-- class=\"[tiny small medium large content]f-dropdown\" -->\n\t\t<ul id=\"drop4\" class=\"medium f-dropdown\" data-dropdown-content>\n\t\t\t<li><a href=\"#\">This is a link</a></li>\n\t\t\t<li><a href=\"#\">This is another</a></li>\n\t\t\t<li><a href=\"#\">Yet another</a></li>\n\t\t</ul>\n\t</div>\n\t<!-- HTML Buttons -->\n\t<div class=\"row\">\n\t\t<h4>Foundation &lt;button&gt;</h4>\n\t\t<button class=\"button expand round\" type=\"button\" value=\"Foundation Button\">Expanded Button</button>\n\t\t<button class=\"button split\" type=\"button\">Split Button <span data-dropdown=\"drop5\"></span><br>\n\t\t\t<ul id=\"drop5\" class=\"f-dropdown\" data-dropdown-content>\n\t\t\t\t<li><a href=\"#\">This is a link</a></li>\n\t\t\t\t<li><a href=\"#\">This is another</a></li>\n\t\t\t\t<li><a href=\"#\">Yet another</a></li>\n\t\t\t</ul></button>\n\n\t\t<h4>HTML Buttons</h4>\n\t\t<!-- Add type=\"[button submit cancel]\" (t=b does not auto-submit\nbutton allows nested HTML. IE may ignore the value, returning content?\nalso allows ::before & ::after, can be disabled -->\n\t\t<button id=\"htmlbutton\" type=\"button\" value=\"h5b\">HTML 5 Button</button>\n\t\t<input id=\"buttonButton\" type=\"button\" value=\"Input Button\">\n\t\t<input id=\"buttonSubmit\" type=\"submit\" value=\"Input Submit\">\n\t\t<input id=\"buttonImage\" type=\"image\" src=\"\" value=\"Input Image\">\n\t\t<input id=\"buttonFile\" type=\"file\" accept=\".jpg,.png,.doc\" value=\"Input File\">\n\t\t<input id=\"buttonReset\" type=\"reset\" value=\"Input Reset\">\n\t</div>\n\n\t<hr>\n\t<!-- Progress Bars -->\n\t<div class=\"row\">\n\t\t<!-- outer classes: class=\"progress small-7] [secondary alert success] [radius round]\" -->\n\t\t<div class=\"progress small-7 alert radius\">\n\t\t\t<span class=\"meter\" style=\"width: 30%\"></span>\n\t\t</div>\n\t\t<div class=\"progress small-7 large-4 secondaryround\">\n\t\t\t<span class=\"meter\" style=\"width: 75%\"></span>\n\t\t</div>\n\t\t<div class=\"progress small-12 success\">\n\t\t\t<span class=\"meter\" style=\"width: 50%\"></span>\n\t\t</div>\n\t</div>\n\n\t<hr>\n\t<!-- -->\n\t<div class=\"row\">\n\t\t<select class=\"form-control\">\n\t\t\t<option>1</option>\n\t\t\t<option>2</option>\n\t\t\t<option>3</option>\n\t\t\t<option>4</option>\n\t\t\t<option>5</option>\n\t\t</select>\n\t\t<br />\n\t\t<select id=\"multiSelect\" multiple=\"multiple\" class=\"form-control\">\n\t\t\t<option>1</option>\n\t\t\t<option>2</option>\n\t\t\t<option>3</option>\n\t\t\t<option>4</option>\n\t\t\t<option>5</option>\n\t\t</select>\n\t</div>\n\t<hr>\n</form>","x":352.4999694824219,"y":1360,"z":"7f7e9fdc.66f4e8","wires":[["86a14bb2.5bbad8"]]},{"id":"ae2e3250.e91b2","type":"function","name":"","func":"msg.payload.pgTitle = \"Foundation Input Tests\"\nreturn msg;","outputs":1,"valid":true,"x":212.5,"y":1360,"z":"7f7e9fdc.66f4e8","wires":[["72fe6d21.9f1e8c"]]},{"id":"6291ffe5.a9c5a8","type":"subflow:59f72869.760188","x":696.4999694824219,"y":1360,"z":"7f7e9fdc.66f4e8","wires":[]},{"id":"3162a56.a800fda","type":"comment","name":"Test Foundation Input Form","info":"","x":133,"y":1320,"z":"7f7e9fdc.66f4e8","wires":[]},{"id":"951539ee.d29bb8","type":"debug","name":"","active":false,"console":"false","complete":"true","x":210,"y":1400,"z":"7f7e9fdc.66f4e8","wires":[]},{"id":"86a14bb2.5bbad8","type":"template","name":"script1 (ws)","field":"payload.script1","format":"handlebars","template":"    <script>\n        // Which websocket path are we interested in? (NB: No leading /)\n        var wsPath = 'input';\n        \n        // Do we want mqtt live updates?\n        mqttGo = true;\n        \n        // this is run when the page recieves input on /ws/<wsPath>\n        var doOnRecieve = function(data) {\n            $(\"#LM\" + data.payload.deviceName).text(data.payload.lastModified);\n            $(\"#T\" + data.payload.deviceName).text(data.payload.Temperature);\n            $(\"#H\" + data.payload.deviceName).text(data.payload.Humidity);\n            $(\"#L\" + data.payload.deviceName).text(data.payload.Light);\n            $(\"#EH\" + data.payload.deviceName).text(data.payload.elapsedh);\n            $(\"#C\" + data.payload.deviceName).text(data.payload.command);\n        };\n        \n        //var doOnConnect = function(){\n    \t//\tconsole.log(\"here\");\n    \t//\treturn \"thisisastring\";\n    \t//}\n        \n    </script>\n","x":503.7833557128906,"y":1359.6167297363281,"z":"7f7e9fdc.66f4e8","wires":[["6291ffe5.a9c5a8"]]}]
```