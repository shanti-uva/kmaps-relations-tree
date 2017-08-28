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
    }
  });
});
```

## Authors

* [Derik](https://github.com/rderik)


## Acknowledgements

* To everyone at [SHANTI](https://github.com/orgs/shanti-uva/people)
