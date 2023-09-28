---
language: en
layout: default
title: "Didactic material"
permalink: /en/materiale.html
---

{%include pageglobal.html %}

## Didactic Material  

> This material has been developed for the students of this course. 
Since knowledge *should* be considered everyone's heritage, my material is available to anyone who wants
to study the course topics. However, such material *cannot be used, even in part, for other purposes
or in other courses*, without my explicit permission and without citing the source.

### Slides  {#slides}

{% if materialinfo.slides %}
<ul>
{% for s in materialinfo.slides %}<li> 
<a href="{{ s.url }}">{% if s.nome[language] %}{{ s.nome[language] }}
{% elsif s.nome['all'] %}{{ s.nome['all'] }}{% endif %}</a>
{% if s.commento[language] %}   <br/><em>{{ s.commento[language] }}</em>
{% elsif s.commento['all'] %}   <br/><em>{{ s.commento['all'] }}</em> 
{% endif %}</li>{% endfor %}
</ul>
{% endif %}

### Final Course Projects  {#progetti}

{% if materialinfo.projects %}
<ul>
{% for s in materialinfo.projects %}<li> 
<a href="{{ s.url }}">{% if s.nome[language] %}{{ s.nome[language] }}
{% elsif s.nome['all'] %}{{ s.nome['all'] }}{% endif %}</a>
{% if s.commento[language] %}   <br/><em>{{ s.commento[language] }}</em>
{% elsif s.commento['all'] %}   <br/><em>{{ s.commento['all'] }}</em> 
{% endif %}</li>{% endfor %}
</ul>
{% endif %}

### Examples  {#esempi}

> Before trying to run or modify these examples, read the [Software](/en/risorse#software) section
and set-up all the required software

{% if materialinfo.examples %}
<ul>
{% for s in materialinfo.examples %}<li> 
<a href="{{ s.url }}">{% if s.nome[language] %}{{ s.nome[language] }}
{% elsif s.nome['all'] %}{{ s.nome['all'] }}{% endif %}</a>
{% if s.commento[language] %}   <br/><em>{{ s.commento[language] }}</em>
{% elsif s.commento['all'] %}   <br/><em>{{ s.commento['all'] }}</em> 
{% endif %}</li>{% endfor %}
</ul>
{% endif %}


{% if courseinfo.testi %}
## Textbooks  {#testi}
{% assign a =  courseinfo.testi | where_exp: "testo","testo.lingua == language" %}
<ul>
{% for testo in a %}<li> <em>{{ testo.autori }}</em>, {{ testo.titolo }}, {{ testo.editore }}   
{% if testo.commento[language] %}   <br/><em>{{ testo.commento[language] }}</em>
{% elsif testo.commento['all'] %}   <br/><em>{{ testo.commento['all'] }}</em> 
{% endif %}</li>{% endfor %}
</ul>
{% endif %}