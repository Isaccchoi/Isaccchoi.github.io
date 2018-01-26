---
layout: post
title: "Bootstrap-datepicker"
date: 2018-01-05 10:08:00 +0800
lang: en
nav: post
category: 모내기
tags: [Python Package, Bootstrap, ]
---

# Bootstrap DatePicker


```javascript
<script>
    $(document).ready(function(){
        $('#id_star_rate').addClass('form-control');
        $('#id_comment').attr("rows", 1);
    });
    $('#date-input').datepicker({
        format: "yyyy-mm-dd",
        startDate: new Date(),
        endDate: "+14d",
        todayBtn: "linked",
        language: "kr"
    }).datepicker("setDate", new Date());
</script>
```
**기본값**에 현재 날짜가 들어가려면 뒤에 있는 `.datepicker("setDate", new Date());`부분을 입력을 해줘야함
