---
layout: page
title: Tags
permalink: /tags/
---

<style>
.tags-navigation {
  margin-bottom: 2em;
}

.tags-content {
  list-style: none;
  padding: 0;
}

.tag-section {
  margin-bottom: 1.5em;
  padding-bottom: 1em;
  border-bottom: 1px solid #eee;
}

.tag-section.single-post .tag-posts {
  display: none;
}

.tag-section.single-post.expanded .tag-posts {
  display: block;
}

.tag-header {
  display: flex;
  align-items: center;
  gap: 0.5em;
  margin-bottom: 0.5em;
}

.tag-title {
  font-weight: bold;
  font-size: 1.2em;
  margin: 0;
}

.tag-more-btn {
  color: #0066cc;
  cursor: pointer;
  font-size: 0.9em;
  user-select: none;
  text-decoration: none;
}

.tag-more-btn:hover {
  text-decoration: underline;
}

.tag-section.single-post .tag-more-btn::before {
  content: "More...";
}

.tag-section.single-post.expanded .tag-more-btn::before {
  content: "Less";
}

.tag-section:not(.single-post) .tag-more-btn {
  display: none;
}

.tag-posts {
  margin-top: 0.5em;
}

.tag-posts .post-item {
  margin: 0.3em 0;
}
</style>

<div class="tags-navigation">
<ul class="tags-box">
{% if site.posts != empty %}
	{% for tag in site.tags %}
		<a href="#{{ tag[0] | url_encode }}" title="{{ tag[0] }}" rel="{{ tag[1].size }}" class="nav-tag-link" data-tag="{{ tag[0] | url_encode }}" data-single="{% if tag[1].size == 1 %}true{% else %}false{% endif %}">{{ tag[0] }}<span class="size"> {{ tag[1].size }}</span></a>
	{% endfor %}
</ul>
</div>

<ul class="tags-content">
	{% for tag in site.tags %}
		<li class="tag-section{% if tag[1].size == 1 %} single-post{% endif %}" id="{{ tag[0] | url_encode }}" data-tag="{{ tag[0] | url_encode }}">
			<div class="tag-header">
				<h2 class="tag-title">{{ tag[0] }}</h2>
				<span class="tag-more-btn"></span>
			</div>
			<div class="tag-posts">
				{% for post in tag[1] %}
					<div class="post-item">
						<time datetime="{{ post.date | date:"%Y-%m-%d" }}">{{ post.date | date:"%Y-%m-%d" }}</time> &raquo;
						<a href="{{ site.baseurl }}{{ post.url }}" title="{{ post.title }}">{{ post.title }}</a>
					</div>
				{% endfor %}
			</div>
		</li>
	{% endfor %}
{% if site.posts == empty %}
<span>No posts</span>
{% endif %}
</ul>

<script>
(function() {
  // 切换单个tag的展开/收起状态
  function toggleTag(tagElement, shouldExpand) {
    if (!tagElement.classList.contains('single-post')) return;

    if (shouldExpand === undefined) {
      tagElement.classList.toggle('expanded');
    } else if (shouldExpand) {
      tagElement.classList.add('expanded');
    } else {
      tagElement.classList.remove('expanded');
    }
  }

  // 处理More按钮点击
  document.querySelectorAll('.tag-more-btn').forEach(function(btn) {
    btn.addEventListener('click', function(e) {
      e.preventDefault();
      e.stopPropagation();
      var tagSection = this.closest('.tag-section');
      toggleTag(tagSection);
    });
  });

  // 处理导航链接点击
  document.querySelectorAll('.nav-tag-link').forEach(function(link) {
    link.addEventListener('click', function(e) {
      var isSingle = this.getAttribute('data-single') === 'true';
      var tagId = this.getAttribute('data-tag');

      if (isSingle) {
        // 如果是单条目tag，展开它
        setTimeout(function() {
          var tagElement = document.getElementById(tagId);
          if (tagElement) {
            toggleTag(tagElement, true);
          }
        }, 10);
      }
    });
  });

  // 处理页面加载时的hash
  function handleHashChange() {
    var hash = window.location.hash.substring(1);
    if (hash) {
      var tagElement = document.getElementById(decodeURIComponent(hash));
      if (tagElement && tagElement.classList.contains('single-post')) {
        toggleTag(tagElement, true);
      }
    }
  }

  // 监听hash变化
  window.addEventListener('hashchange', handleHashChange);

  // 页面加载时检查hash
  if (window.location.hash) {
    handleHashChange();
  }
})();
</script>
