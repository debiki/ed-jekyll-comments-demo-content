---
layout: post
title:  "Demo and installation instructions"
date:   2018-01-09 07:00:00 +0000
discussion_id: demo-and-inst-instrs
---

Talkyard is a commenting system for Jekyll and other static site generators.
It's a Disqus alternative, but [open source](https://github.com/debiki/talkyard/);
you can install it for free on your own server.
Or use our servereless [hosting](https://www.talkyard.io/blog-comments) — no ads, no tracking, free for low traffic blogs.
<!-- Lightweight, just 140 kb javascript (compared with Disqus, about 750 kb). -->

This website is a Jekyll blog, with Talkyard blog comments — look at the bottom of the pages.
Talkyard is forum software too, with chat and question-answers features:
you can create a community for your website, integrated with the blog comments.

Demo video:

<iframe src="https://player.vimeo.com/video/249611399" width="684" height="385" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>

<!--
<iframe src="https://player.vimeo.com/video/249611399" width="640" height="360" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>
<p><a href="https://vimeo.com/249611399">ed-emb-cmts-(3)</a> from <a href="https://vimeo.com/user78434986">Magnus Lindberg</a> on <a href="https://vimeo.com">Vimeo</a>.</p>

<iframe width="684" height="385" src="https://www.youtube.com/embed/2L0eYcsCcbE" frameborder="0" gesture="media" allow="encrypted-media" allowfullscreen></iframe>
-->

<br>
<a href="https://www.kajmagnus.blog/new-embedded-comments">Example discussion (the one in the video).</a>
<br>
<br>

### Quick test if this is for you

Three steps for trying out Talkyard, without signing up or getting your own server:

1. Add this to your `_config.yml` file:

   ```
   talkyard_server_url: https://comments-demo.talkyard.io
   ```

2. Do real installation step 3 below, i.e. add the `_includes/talkyard-comments.html` file.

3. Do real installation step 4 below, i.e. start including that file. **Restart** Jekyll afterwards.

Now, regenerate your blog and look at the comment section that should appear below the blog posts. You can post test comments **but** they'll disappear later on, some day.

Support forum here: <https://www.talkyard.io/forum/latest/support>

If you like it, then do real installation step 1 below, and step 2 again — and this time, specify the address to your own Talkyard site. (Skip step 3 and 4, you've done them already.)
<br>
<br>

### Real installation

Install this commenting system in four steps:

1. Go to <https://www.talkyard.io/plans>, chose *Blog comments* and type your website address.
   Copy the address to your new embedded comments site.

2. In your Jekyll site configuration, i.e. `_config.yml`, add this config value and paste the address:

   ```
   talkyard_server_url: https://comments-for-your-site.talkyard.net
   ```

3. Create a file `_includes/talkyard-comments.html`: (TEST001 is intentional)
   {% raw %}
   ```
   TEST001
   {% if site.talkyard_server_url %}
   {% capture script_url %}{%
     if site.talkyard_script_url %}{{ site.talkyard_script_url }}{%
     else %}{{ 'https://c1.ty-cdn.net/-/talkyard-comments.min.js' }}{%
     endif %}{%
   endcapture %}

   <script>talkyardServerUrl='{{ site.talkyard_server_url }}';</script>
   <script async defer src="{{ script_url }}"></script>
   <div class="talkyard-comments" data-discussion-id="{{ page.discussion_id }}" style="margin-top: 45px;">
   <noscript>Please enable Javascript to view comments.</noscript>
   <p style="margin-top: 25px; opacity: 0.9; font-size: 96%">Comments powered by
   <a href="https://www.talkyard.io">Talkyard</a>.</p>
   </div>
   {% endif %}
   ```
   {% endraw %}

4. Add this in your post template, i.e. `_layouts/post.html`, where you want comments to appear:

   {% raw %}
   ```
   {% include talkyard-comments.html %}
   ```
   {% endraw %}

   If you don't have a `_layout/posts.html` file, that's because by default Jekyll hides it.
   Read more here: <https://jekyllrb.com/docs/themes/#overriding-theme-defaults> about where
   you'll find it (and you need to copy it to your directory).

5. Optionally, add a frontmatter `discussion_id: per-discussion-id` to your blog posts / articles.
   Then, you can change the URL to a blog post, without the discussion disappearing.

Now, **restart Jekyll** and reload a blog post in the browser. Do you see a comments section now?
If so, remove TEST001 above. If not — do you see TEST001? If you *do* see TEST001 but not the comments,
then ask for help, see below. If you don't see TEST001, you added the comments code at the wrong place,
or you're looking at the wrong page.

You can ask for help in [the support forum][support-cat], and [suggest ideas][ideas-cat].


[support-cat]: https://www.talkyard.io/forum/latest/support
[ideas-cat]: https://www.talkyard.io/forum/latest/ideas
