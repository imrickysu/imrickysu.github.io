---
layout: page
title: Tags
permalink: /tags/
---

<ul class="tags-box" id="tags-nav">
{% if site.posts != empty %}
	{% for tag in site.tags %}
		<a href="#{{ tag[0] | url_encode }}" title="{{ tag[0] }}" rel="{{ tag[1].size }}" class="tag-link {% if tag[1].size == 1 %}single-item collapsed{% endif %}" data-tag="{{ tag[0] | url_encode }}">{{ tag[0] }}<span class="size"> {{ tag[1].size }}</span></a>
	{% endfor %}
	<button id="toggle-nav-tags" class="more-button">More...</button>
</ul>

<ul class="tags-box" id="tags-content">
	{% for tag in site.tags %}
		<li id="{{ tag[0] | url_encode }}" class="tag-section {% if tag[1].size == 1 %}single-item collapsed{% endif %}">{{ tag[0] }}</li>
		<div class="tag-posts {% if tag[1].size == 1 %}single-item collapsed{% endif %}">
		{% for post in tag[1] %}
			<time datetime="{{ post.date | date:"%Y-%m-%d" }}">{{ post.date | date:"%Y-%m-%d" }}</time> &raquo;
			<a href="{{ site.baseurl }}{{ post.url }}" title="{{ post.title }}">{{ post.title }}</a><br />
		{% endfor %}
		</div>
	{% endfor %}
	<button id="toggle-content-tags" class="more-button">More...</button>
{% else %}
<span>No posts</span>
{% endif %}
</ul>

<script>
(function() {
  const navToggle = document.getElementById('toggle-nav-tags');
  const contentToggle = document.getElementById('toggle-content-tags');
  const navTags = document.querySelectorAll('#tags-nav .tag-link.single-item');
  const contentSections = document.querySelectorAll('#tags-content .single-item');

  let isExpanded = false;

  function updateButtons() {
    if (isExpanded) {
      navToggle.textContent = 'Less...';
      contentToggle.textContent = 'Less...';
    } else {
      navToggle.textContent = 'More...';
      contentToggle.textContent = 'More...';
    }
  }

  function toggleTags() {
    isExpanded = !isExpanded;

    navTags.forEach(tag => {
      if (isExpanded) {
        tag.classList.remove('collapsed');
      } else {
        tag.classList.add('collapsed');
      }
    });

    contentSections.forEach(section => {
      if (isExpanded) {
        section.classList.remove('collapsed');
      } else {
        section.classList.add('collapsed');
      }
    });

    updateButtons();
  }

  navToggle.addEventListener('click', toggleTags);
  contentToggle.addEventListener('click', toggleTags);

  // When clicking a collapsed tag in nav, auto-expand content
  document.querySelectorAll('#tags-nav .tag-link').forEach(link => {
    link.addEventListener('click', function(e) {
      const tagId = this.getAttribute('data-tag');
      const isSingleItem = this.classList.contains('single-item');

      if (isSingleItem && !isExpanded) {
        // Expand all tags
        toggleTags();
      }
    });
  });

  updateButtons();
})();
</script>
