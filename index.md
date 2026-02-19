---
title: Home
layout: default
---

## AI Notepad Block 🧠

Meu bloco de notas sobre Inteligência Artificial. Aqui registro o que aprendo, experimento e construo.

---

### Posts recentes

{% assign sorted_posts = site.posts | sort: 'date' | reverse %}
{% for post in sorted_posts limit:10 %}
- `{{ post.date | date: "%Y-%m-%d" }}` [{{ post.title }}]({{ post.url | relative_url }}) — *{{ post.category }}*
{% endfor %}

{% if site.posts.size == 0 %}
*Nenhum post ainda. Em breve...*
{% endif %}

---

📂 [Ver todas as categorias]({{ '/categorias' | relative_url }})
