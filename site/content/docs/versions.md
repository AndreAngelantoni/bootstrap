---
title: Versions
description: An appendix of hosted documentation for nearly every release of Bootstrap, from v1 through v5.
---
<p>We will release bug and security fixes for the current version (v5). The previous version (v4) will be end-of-life on December 1, 2024 and will no longer receive bug or security fixes.</p>
<p>Our partner, HeroDevs, provides commercial security fixes for all unsupported versions (<a href="https://www.herodevs.com/support/nes-bootstrap?utm_source=Bootstrap_site&utm_medium=Banner&utm_campaign=v3and4_eol">www.herodevs.com</a>).</p>
{{< list-versions.inline >}}
<div class="row">
  {{- range $release := sort (index $.Site.Data "docs-versions") "group" "desc" }}
  <div class="col-md-6 col-lg-4 col-xl mb-4">
    <h2>{{ $release.group }}</h2>
    <p>{{ $release.description }}</p>
    <p>{{ if or (eq $release.group "v4.x") (eq $release.group "v3.x") (eq $release.group "v2.x") }}<a href="https://www.herodevs.com/support/nes-bootstrap?utm_source=Bootstrap_site&utm_medium=Banner&utm_campaign=v3and4_eol">Get Commercial Support</a>{{ end }}</p>
    {{- $versions := sort $release.versions "" "desc" -}}
    {{- range $i, $version := $versions }}
      {{- $len := len $versions -}}
      {{ if (eq $i 0) }}<div class="list-group">{{ end }}
        <a class="list-group-item list-group-item-action py-2 text-primary{{ if (eq $version $.Site.Params.docs_version) }} d-flex justify-content-between align-items-center{{ end }}" href="{{ urls.JoinPath $release.baseurl $version "/" }}">
          {{ $version }}
          {{ if (eq $version $.Site.Params.docs_version) -}}
          <span class="badge text-bg-primary">Latest</span>
          {{- end }}
        </a>
      {{ if (eq (add $i 1) $len) }}</div>{{ end }}
    {{ end -}}
  </div>
  {{ end -}}
</div>
{{< /list-versions.inline >}}
