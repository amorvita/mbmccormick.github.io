---
layout: page
title: Search
---

<div id="cse" style="width: 100%;">Loading</div>
<script src="http://www.google.com/jsapi" type="text/javascript"></script>
<script type="text/javascript"> 
  google.load('search', '1', {language : 'en', style : google.loader.themes.MINIMALIST});
  google.setOnLoadCallback(function() {
    var customSearchControl = new google.search.CustomSearchControl(
      '014860799161794631858:puc-rt_9-wc');

    customSearchControl.setResultSetSize(google.search.Search.FILTERED_CSE_RESULTSET);
    customSearchControl.draw('cse');
  }, true);
</script>
