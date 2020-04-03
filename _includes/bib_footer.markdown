## References

{% bibliography --cited %}

## Cite this post

If you'd like to cite this post, please use the following <button class="btn--info" onclick="showBibtex('{{ 12345 }}')">BibTex</button>.

{% assign num = page.url | size | minus: 1 %}
{% assign citekey = page.url | replace: "/", "_" | slice: 0, num %}

<div class="bibtex" style="display:none;" id='{{ 12345 }}'>
<pre>
@misc{Rogers{{ citekey }},
  title = { {{ page.title }}},
  journal = {Hacking Semantics},
  url = { https://hackingsemantics.xyz{{page.url}} },
  author = {Rogers, Anna},
  day = { {{page.date | date: "%d"}} },
  month = { {{page.date | date: "%b"}} },
  year = { {{ page.date | date: "%Y" }} }
}
</pre>
</div>