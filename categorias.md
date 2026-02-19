---
title: Categorias
layout: default
---

<style>
.cat-section { margin-bottom: 2em; }
.cat-header { display: flex; align-items: center; gap: 0.5em; margin-bottom: 0.2em; }
.cat-header h3 { margin: 0; }
.cat-desc { color: #888; font-size: 0.9em; margin-bottom: 0.5em; }
.cat-posts { list-style: none; padding: 0; }
.cat-posts li { padding: 0.3em 0; border-bottom: 1px dashed #333; }
.cat-posts li:last-child { border-bottom: none; }
.cat-date { color: #666; font-family: monospace; font-size: 0.85em; }
.cat-count { color: #666; font-size: 0.8em; }
</style>

{% assign categories_info = "fundamentos:🧠:Redes neurais, transformers, embeddings e conceitos base|llms:🤖:GPT, Claude, modelos de linguagem e como funcionam|prompting:✍️:Técnicas de prompt engineering e exemplos práticos|rag:🔍:Retrieval Augmented Generation e busca semântica|agentes:⚡:Agentes autônomos, tool use e automação com IA|projetos:🛠️:Coisas que construí e experimentei" | split: "|" %}

{% for cat_info in categories_info %}
{% assign parts = cat_info | split: ":" %}
{% assign cat_name = parts[0] %}
{% assign cat_emoji = parts[1] %}
{% assign cat_desc = parts[2] %}
{% assign cat_posts = site.posts | where: "category", cat_name | sort: "date" | reverse %}

<div class="cat-section">
<div class="cat-header">
<h3>{{ cat_emoji }} {{ cat_name | capitalize }}</h3>
<span class="cat-count">({{ cat_posts.size }})</span>
</div>
<p class="cat-desc">{{ cat_desc }}</p>

{% if cat_posts.size > 0 %}
<ul class="cat-posts">
{% for post in cat_posts %}
<li><span class="cat-date">{{ post.date | date: "%Y-%m-%d" }}</span> → <a href="{{ post.url | relative_url }}">{{ post.title }}</a></li>
{% endfor %}
</ul>
{% else %}
<p style="color: #555; font-size: 0.9em;">Nenhum post ainda.</p>
{% endif %}
</div>
{% endfor %}
