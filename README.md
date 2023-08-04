Unofficial attempt to diagram the [European Learning Model](https://github.com/european-commission-empl/European-Learning-Model) data model using [Mermaid](https://mermaid.js.org/) [Class diagram](https://mermaid.js.org/syntax/classDiagram.html).

I found it best to treat classification as a reference to Concepts as a characteristic rather than relationship as it reduces number of links very much.

The result [ELM model visual](elm_model_visual.md) is an entirely unusable cluttered mess due to the size of the model. However is it pretty easy to copy out bits of it to get useful local views, e.g. of the neighbourhood around [Learning Opportunity](elm_learningOp_visual.md)

Starting point is the [ELM RDF Ontology](https://github.com/european-commission-empl/European-Learning-Model/tree/master/rdf/ontology) turtle representation. 

turtle2mermaid.ipynb is a jupyter notebook that builds mermaid markdown for properties and relations where the domain and range are declared in the .ttl file; it also tries to identify the share properties from comments, but this relies on consistent marking of the comment lines (e.g. using `###` before a list of shared properties)—which is not always the case in the original ttl file.