---
layout: post
title:  "Second Task: Query Linked Data (Advanced)"
date:   2026-09-18
categories: jekyll update
---

# SPARQL Endpoint of Wikidata 

1. Please visit: [https://query.wikidata.org](https://query.wikidata.org)

2. Click on "Beispiele" and select one of them. Afterwards click on the Play button. 

3. Make you familiar with the UI and the results. 



# Custom SPARQL Search 

1. Copy the Sparql Query 

2. Paste it in the SPARQL Window. 

3. Press Enter.

- Pro Tip: 
If you want a explaination or change of the SPARQL query, copy it into the AI Mode of Google or Ecosia AI. 
Be aware that this works generally good, but LLM's struggle often with URI's and hallucinate them. 


{% highlight sparql %}
SELECT DISTINCT ?item ?qid ?EPPOCode ?labelEn ?labelDe ?descEn ?descDe
    WHERE {% raw %}{{% endraw %}
      ?item wdt:P3031 ?EPPOCode.
      OPTIONAL {% raw %}{{% endraw %}?item rdfs:label ?labelEn . FILTER(LANG(?labelEn) = "en") {% raw %}}{% endraw %}
      OPTIONAL {% raw %}{{% endraw %}?item rdfs:label ?labelDe . FILTER(LANG(?labelDe) = "de") {% raw %} } {% endraw %} 
      OPTIONAL {% raw %} { {% endraw %} ?item schema:description ?descEn . FILTER(LANG(?descEn) = "en") {% raw %}}{% endraw %}
      OPTIONAL {% raw %} { {% endraw %}?item schema:description ?descDe . FILTER(LANG(?descDe) = "de") {% raw %}}{% endraw %}
      BIND(STRAFTER(STR(?item), "entity/") AS ?qid)
     {% raw %}}{% endraw %}
    LIMIT 10
{% endhighlight %}




