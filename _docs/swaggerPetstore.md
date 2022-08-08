---
title: Markdown reference example
layout: tabs 
---
<div class="productHead">
    <p>Static Data API</p>
</div>
<div class="tabbed">
    <input type="radio" id="tab1" name="css-tabs" checked>
    <input type="radio" id="tab2" name="css-tabs">
    
    <ul class="tabs">
        <li class="tab"><label for="tab1">Reference</label></li>
        <li class="tab"><label for="tab2">API Specification</label></li>
    </ul>
    
    <div class="tab-content">
        <iframe src="{{ "/jargon/jargon_SwaggerPetstore_specificationPage" | prepend: site.baseurl }}"></iframe>
    </div>
    
    <div class="tab-content">
        <iframe src="{{ "/docs/openapi?spec=" | append: site.baseurl | append:"/jargon/jargon_SwaggerPetstore_openapi.json" | prepend: site.baseurl }}"></iframe>
    </div>
    
</div>
