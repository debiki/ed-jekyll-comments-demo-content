---
layout: post
title:  "Demo and installation instructions"
date:   2018-01-02 10:05:04 +0000
discussion_id: installation-instructions
---

This is a new commenting system for Jekyll and other static site generators. It's called ed-comments (ed = Effective Discussions) and it's [open source](https://github.com/debiki/ed-server/) so you can install it for free on your own server. There's hosting too, so it's serverless. No ads, no tracking. Lightweight, just 140 kb javascript (in comparison to Disqus' about 750 kb).

This website is a static Jekyll blog, with ed-comments below each blog post.

Demo video:

<iframe src="https://player.vimeo.com/video/249611399" width="684" height="385" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>

<!--
<iframe src="https://player.vimeo.com/video/249611399" width="640" height="360" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>
<p><a href="https://vimeo.com/249611399">ed-emb-cmts-(3)</a> from <a href="https://vimeo.com/user78434986">Magnus Lindberg</a> on <a href="https://vimeo.com">Vimeo</a>.</p>

<iframe width="684" height="385" src="https://www.youtube.com/embed/2L0eYcsCcbE" frameborder="0" gesture="media" allow="encrypted-media" allowfullscreen></iframe>
-->

<br>

### Quick test if this is for you

Maybe you don't want to get a server and install, or sign up for our hosted service,
just to find out if ed-comments works for your blog / website?

Here're 3 quick steps for you to try out ed-comments:

1. Add this to your `_config.yml` file:

   ```
   ed_comments_server_url: https://comments.demo.ed.community
   ```

2. Do real installation step 3 below, i.e. add the `_include/ed-comments.html` file.

3. Do real installation step 4 below, i.e. start including that file.

Now, regenerate your blog and look at the comment section that shoud now appear below the blog posts.
Are you satisfied with how it looks? If not, please tell us/me: <https://www.ed.community/forum/> :- P.
Currently the comment section background color is always white, but later on you'll be able to tweak how it looks.

You can post test comments **but** they'll disappear later on some day.

If you like it, then do real-installation-step-1 below, and step 2 again, but this time, specify the
address to your own ed-comments site.


### Real installation

Install this commenting system in four steps:

1. Go to <https://www.ed.community> and click Create Community, choose Blog Comments and type your website address.
   Copy the address to your new embedded comments site.

2. Then, in your Jekyll site configuration, i.e. `_config.yml`, add a config value and paste the address, like so:

   ```
   ed_comments_server_url: https://comments-for-your-site.ed.community
   ```

3. Create a file `_includes/ed-comments.html`:
   {% raw %}
   ```
   {% if site.ed_comments_server_url %}
   {% capture script_url %}{%
     if site.ed_comments_script_url %}{{ site.ed_comments_script_url }}{%
     else %}{{ 'https://edc-49f8.kxcdn.com/-/ed-comments.min.js' }}{%
     endif %}{%
   endcapture %}

   <script>edCommentsServerUrl='{{ site.ed_comments_server_url }}';</script>
   <script async defer src="{{ script_url }}"></script>
   <div class="ed-comments" data-discussion-id="{{ page.discussion_id }}" style="margin-top: 45px;">
   <noscript>Please enable Javascript to view comments.</noscript>
   <p style="margin-top: 25px; opacity: 0.9; font-size: 96%">Comments powered by
   <a href="https://www.effectivediscussions.org">Effective Discussions</a>.</p>
   </div>
   {% endif %}
   ```
   {% endraw %}

4. Add this in your post template, i.e. `_layouts/post.html`, where you want comments to appear:

   {% raw %}
   ```
   {% include ed-comments.html %}
   ```
   {% endraw %}

5. Optionally, add a frontmatter `discussion_id: per-discussion-id` to your blog posts / articles.
   Then, you can change the URL to the page, without the discussion disappearing.

You can ask for help in [the support forum][support-forum].

[support-forum]: https://www.effectivediscussions.org/forum/latest/support
