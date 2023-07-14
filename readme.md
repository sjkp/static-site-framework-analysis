

Query from play.clickhouse.com 

```
SELECT repo_name, makeDate(toYear(created_at), toMonth(created_at), 1), count() FROM github_events WHERE event_type = 'WatchEvent' AND repo_name IN ('facebook/docusaurus',
'gatsbyjs/gatsby',
'withastro/astro',
'gridsome/gridsome',
'hexojs/hexo',
'honojs/hono',
'gohugoio/hugo',
'jekyll/jekyll',
'vercel/next.js',
'nuxt/nuxt',
'getpelican/pelican',
'preactjs/preact',
'builderio/qwik',
'facebook/react',
'remix-run/remix',
'solidjs/solid',
'sveltejs/svelte',
'vitejs/vite',
'vuejs/core',
'vuejs/vuepress',
'getzola/zola',
'angular/angular',
'elderjs/elderjs',
'11ty/eleventy',
'mkdocs/mkdocs',
'emberjs/ember.js') GROUP BY repo_name, makeDate(toYear(created_at), toMonth(created_at), 1)
```

To download the data in json format you can create a http request with the following syntax

```
GET /?user=play&default_format=JSON HTTP/1.1
Host: play.clickhouse.com
Content-Type: text/plain
Content-Length: 710

SELECT repo_name, makeDate(toYear(created_at), toMonth(created_at), 1), count() FROM github_events WHERE event_type = 'WatchEvent' AND repo_name IN ('facebook/docusaurus',
'gatsbyjs/gatsby',
'withastro/astro',
'gridsome/gridsome',
'hexojs/hexo',
'honojs/hono',
'gohugoio/hugo',
'jekyll/jekyll',
'vercel/next.js',
'nuxt/nuxt',
'getpelican/pelican',
'preactjs/preact',
'builderio/qwik',
'facebook/react',
'remix-run/remix',
'solidjs/solid',
'sveltejs/svelte',
'vitejs/vite',
'vuejs/core',
'vuejs/vuepress',
'getzola/zola',
'angular/angular',
'elderjs/elderjs',
'11ty/eleventy',
'mkdocs/mkdocs',
'emberjs/ember.js') GROUP BY repo_name, makeDate(toYear(created_at), toMonth(created_at), 1)
```



Github query selector for gettting all people from and organization page
https://github.com/orgs/atc-net/people?page=2

Array.from(document.querySelectorAll('[data-test-selector="linked-name-is-full-if-exists"]')).map(s => s.id).map((s => s.replace('member-',''))).join('\',\'')

```
SELECT
    repo_name,
    created_at,
    actor_login
FROM github_events
WHERE (event_type = 'WatchEvent') AND (actor_login = 'sjkp') AND (repo_name IN
(
    SELECT repo_name
    FROM github_events
    WHERE (event_type = 'WatchEvent') AND (actor_login = 'sjkp')
))
ORDER BY created_at DESC
LIMIT 50
```