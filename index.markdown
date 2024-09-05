---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---
<p>
Hey there! Thanks for taking the time to check out my website.
</p>

<h1>Latest Posts (By category):</h1>

{% for category in site.categories %}
<h1> {{ category | first }} </h1>
<ul>
{% for posts in category | first %}

{% for post in posts %}
{% if post.url %}
<li>
<a href= "{{ post.url }}">
<time> {{post.date | date: "%-d %B %Y" | reverse }}</time>
  - {{post.title}}
 </a>
</li>
{% endif %}
{%endfor%}
{%endfor%}
</ul>



{%endfor %}