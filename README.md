# Kmaps Relations Tree

This project contains a jQuery plugin that requires [fancytree](https://github.com/mar10/fancytree) to display the hierarchical relations tree for the SHANTI Knowledge Maps applications, you can read more [here](https://shanti.virginia.edu/wordpress/?page_id=4023) and visit the [Mandala tools here](https://mandala.shanti.virginia.edu/), the relations tree you see on the related features (Places for places or Subjects for subjects) is what this pluging takes care of.

This plug-in works differently than [Kmaps Tree](https://github.com/shanti-uva/kmaps-tree) this tree shows all the relations for the descendants while the [Kmaps Tree](https://github.com/shanti-uva/kmaps-tree) just shows the descendants for the current perspective and works best for the fly-out, make sure you are using the appropiate depending on your needs.

## Getting Started

To add this plug-in to your Kmaps application you can download the code from the git repository:
* [https://github.com/shanti-uva/kmaps-relations-tree](https://github.com/shanti-uva/kmaps-relations-tree)

You can clone it or just download the jQuery plug-in.

### Prerequisites

The plug-in requires:

* Kmaps app (this plug-in was designed for the KMAPS apps so you need an instance for it to run)
* Solr index where the tree data is stored (and consulted)
* [fancytree](https://github.com/mar10/fancytree)

You'll notice that there is now CSS provided, it should be part of your KMAPS app.

### How to use it:

```
$(document).ready(function(){
  $("#relation_tree_container").kmapsRelationsTree({
    domain: "YOUR_APP_DOMAIN", //[places, subjects, sources, etc.]
    featureId: "FID", //Feature fid of the active node
    featuresPath: "HTTPS://PATH/TO/NODE/%%ID%%", //This base URL is a pattern with the %%ID%% to be replaced with each node's ID
    perspective: "PERSPECTIVE.CODE",
    tree: "TREE_ID_IN_SOLR", //[places,subjects,sources, etc.]
    termIndex: "HTTPS://SERVER/PATH/TO/TERM_INDEX",
    seedTree: {
      descendants: true, //Show descendants
      directAncestors: false, //Show only direct A
    },
    displayPopup: false,
    mandalaURL: "https://mandala.shanti.virginia.edu/%%APP%%/%%ID%%/%%REL%%/nojs"
  });
});
```

### Modifications for pop-up

all the pop-up decoration is done in the function: `decorateElementWithPopover` something important to note is that currently the links to the associated features is hard coded but it can easily be modified for this search for the `shown.bs.popover` action in the `decorateElementWithPopover` function, there you'll find the list of features that the popover show and just replace the link with what ever you need.

For example:
```
            popOverFooter.append("<div style='display: none' class='popover-footer-button'><a href='"+plugin.options.featuresPath.replace("%%ID%%",key.replace(plugin.options.domain+'-',""))+"#show_relationship=subjects' class='icon shanticon-subjects' target='_blank'>Related subjets (<span class='badge-count' >?</span>)</a></div>");
```

the link href is using the featuresPath URL but it can easily be changed to some other app link for example using the `mandlaURL`

```
            popOverFooter.append("<div style='display: none' class='popover-footer-button'><a href='"+plugin.options.mandalaURL.replace("%%ID%%",key.replace(plugin.options.domain+'-',"")).replace("%%APP%%",plugin.options.domain).replace("%%REL%%","subjects")+"' class='icon shanticon-subjects' target='_blank'>Related subjets (<span class='badge-count' >?</span>)</a></div>");
```


## Authors

* [Derik](https://github.com/rderik)


## Acknowledgements

* To everyone at [SHANTI](https://github.com/orgs/shanti-uva/people)
