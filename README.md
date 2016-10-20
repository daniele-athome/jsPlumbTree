jsPlumbTree
===========

A jQuery plugin for generating a tree structure using [jsPlumb](https://github.com/jsplumb/jsPlumb/).
The tree is drawn from left to right, top to bottom.

**Please note that only jsPlumb up to version 1.7.x is supported!!**


Usage
=====

Initialization should be done in the jsPlumb ready callback:

```
jsPlumb.ready(function() {
    // get an instance of jsPlumb first
    var pdef = {
        // disable dragging
        DragOptions: null,
        // tree container id (with all the nodes)
        Container : "container"
    };
    var plumb = jsPlumb.getInstance(pdef);

    var opts = {
        // node objects id prefix
        prefix: 'node_',
        // left coordinate of root node (0)
        baseLeft: 0,
        // top coordinate of root node (0)
        baseTop: 0,
        // node width
        nodeWidth: 100,
        // horizontal padding between nodes
        hSpace: 36,
        // vertical padding between nodes
        vSpace: 10,
        // source anchor
        sourceAnchor: "RightMiddle",
        // target anchor
        targetAnchor: "LeftMiddle",
        // source endpoint definition
        sourceEndpoint: null,
        // target endpoint definition
        targetEndpoint: null,
        // image url for plus anchor button
        imgPlus: null,
        // image url for minus anchor button
        imgMinus: null,
        // a function(this, node) to be called before making a connection
        connectFunc: null,
        // ...add other jsPlumb options here...
    };

    var tree = jQuery.jsPlumbTree(plumb, opts);
    tree.init();
});
```

All nodes must have the following HTML attributes set:

* data-id: node id. Must be unique in the whole tree
* data-parent: parent node id. Do not set for the root node
* data-first-child: id of the first child node
* data-next-sibling: id of the next sibling node
