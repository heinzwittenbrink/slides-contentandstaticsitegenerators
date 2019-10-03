---
title: Content First und Static Site Generators
author: Heinz Wittenbrink
date: 2019-09-28
---

# Was sind Static Site Generators


##

- Website wird lokal generiert
- Statische Auslieferung
- Verbindung mit Microservices

##

- Markdown und andere Textinhaltsformate
- Template-Sprachen

## Vorteile

- Geschwindigkeit
- Leichte Entwicklung

## Jekyll und Hugo

- Jekyll: Erster erfolgreicher SSG, enge Verbindung zu GitHub
- Hugo: Hohe Performanz und Flexibilität

# Beispielprojekt

##

Repository: <https://github.com/heinzwittenbrink/offgallery_at>
Daten der Website: <https://github.com/heinzwittenbrink/offgallery_at/tree/master/_site>
Testversion: <https://silly-hypatia-0d5c1f.netlify.com/>

## eleventy

- [Eleventy](https://www.11ty.io/ "Eleventy")
- Basis: JavaScript, NodeJS
- Unterstützt viele Templatesprachen

## Installation

- [Getting Started—Eleventy](https://www.11ty.io/docs/getting-started/ "Getting Started—Eleventy")
- Lokale oder globale Installation

## Generieren der Site

##

Beispiel: Starten von eleventy mit lokalem Server

```bash
eleventy --serve

```

## Ordnerstruktur

![](pics/folders_eleventy_content.png){ width=70% }

## Content als Markdown

```markdown
---
layout: picture_desc.njk
tags: thepromiseofthecity
artist: Martin Grabner
rights: Martin Grabner
gallery:
- martin-grabner-transformation-ldn
title: Transformation LDN
author: Martin Grabner
---


Londons Straßen nahe der City harren der unvermeidlichen Gentrifizierung. Inzwischen steht in dieser Baulücke in der Clerkenwell Road ein mehrgeschoßiges Geschäftshaus.

```

## Frontmatter/tags

![](pics/eleventy_front_matter.png){ width=70% }

## Directory data

```json
{
  "layout" : "article.njk",
  "changefreq": "monthly",
  "priority": "0.9"
}
```

## RSS-Feed

```markdown
---
permalink: feed.xml
eleventyExcludeFromCollections: true

metadata:
  title: off_gallery.at
  url: https://offgallery.at/
  author:
    name: Anastasija Georgi, Erika Petrić, Heinz Wittenbrink
    email: info@offgallery.at
  feed:
    subtitle: offgallery_graz - Nachrichten und Einladungen
    filename: feed.xml
    path: feed/feed.xml
    url: https://offgallery.at/feed.xml
    id: https://offgallery.at/
---
<?xml version="1.0" encoding="utf-8"?>
<feed xmlns="http://www.w3.org/2005/Atom">
  <title>{{ metadata.title }}</title>
  <subtitle>{{ metadata.feed.subtitle }}</subtitle>
  <link href="{{ metadata.feed.url }}" rel="self"/>
  <link href="{{ metadata.url }}"/>

```

## Sitemap

```markdown
---
permalink: /sitemap.xml
eleventyExcludeFromCollections: true
---
<?xml version="1.0" encoding="utf-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
{%- for page in collections.all %}
  {% set absoluteUrl %}{{ page.url | url | absoluteUrl(metadata.url) }}{% endset %}
  <url>
    <loc>{{ absoluteUrl }}</loc>
    <lastmod>{{ page.date | htmlDateString }}</lastmod>
  </url>
{%- endfor %}
</urlset>

```

# SSG-Ökosystem

## Netlify

## Forestry


# Verbindung von CMS und SSGs

##

> I’m going out on a limb by saying we may be on the cusp of a revolution as it relates to how we build, deploy and manage websites.

Mark Figgart [Pairing Static Websites with CMS](https://www.digett.com/insights/pairing-static-websites-cms)



## Vorteile von SSGs

## Tempo

> First, static sites are blazing fast. A web server tasked with serving static sites can run circles around a web server bogged down with executing server-side scripts and making twenty-plus database queries per HTTP request. It’s an all-too-common scenario.

Mark Figgart  [Pairing Static Websites with CMS | Digett](https://www.digett.com/insights/pairing-static-websites-cms)  (2014)

## Sicherheit

> static sites typically don’t expose the vulnerabilities that so often come with a site dependent on execution of scripts like PHP and ASP.net and running on the public Internet

Mark Figgart  [Pairing Static Websites with CMS | Digett](https://www.digett.com/insights/pairing-static-websites-cms)  (2014)

## Nachteile

> Unfortunately, static websites don’t lend themselves to the serious work some might demand of, say, a mission-critical sales and marketing tool.

Mark Figgart: [Pairing Static Websites with CMS](https://www.digett.com/insights/pairing-static-websites-cms)  (2014)

##

> Let’s sum it up this way: Static sites offer no inherent build and management interface.

Mark Figgart: [Pairing Static Websites with CMS](https://www.digett.com/insights/pairing-static-websites-cms)

## Vorteile typischer Content Management Systeme

- Nutzerverwaltung
- Rechte-Administration
- Inhaltsmodellierung
- Aktualisierung und Versionsverwaltung
- URL Handling

Mark Figgart [Pairing Static Websites with CMS](https://www.digett.com/insights/pairing-static-websites-cms)


##

> Untuned, a CMS can be disappointingly slow. The traditional solution has been to throw more technology on the stack in the form of high-performance caching mechanisms. In essence, these solutions create, you guessed it, a "static” version of the site, and serve pages from it in response to requests.

Mark Figgart [Pairing Static Websites with CMS](https://www.digett.com/insights/pairing-static-websites-cms)



##

> Practically speaking, however, these caching solutions tend to be complex and expensive.

Mark Figgart: [Pairing Static Websites with CMS](https://www.digett.com/insights/pairing-static-websites-cms)

##

> So what if we could assemble an approach to building, deploying and managing websites with all the benefits of static files — including speed and security — with the robust build and management capabilities of a tool like Wordpress or Drupal?

Mark Figgart: [Pairing Static Websites with CMS](https://www.digett.com/insights/pairing-static-websites-cms)

##

> we extract a static representation of the site’s output in the form of a complete file and folder hierarchy. This static version of the site is what gets pushed to the web server.

Mark Figgart: [Pairing Static Websites with CMS](https://www.digett.com/insights/pairing-static-websites-cms)



# Support von SSGs durch Contenful

##

> We love static sites and have plugins to support four of our favorites.

[Static site generators – Contentful](https://www.contentful.com/developers/docs/tools/staticsitegenerators/)

## Tools


- Plugins für Middleman, Jekyll, Gatsby, Metalsmith
- Nicht offiziell supportete Plugins für Roots und AWS Lambda
- Nicht offizieller Simple Static Site Generator (*A CLI tool to generate a site from templates and data in a Contentful space*)

## Exportieren

[Importing and exporting content with the Contentful CLI – Contentful](https://www.contentful.com/developers/docs/tutorials/cli/import-and-export/)



# Fragen

## Unterstützen SSGs das Prinzip *Content First* besser als andere CMS?

## Welchen Support bieten sie für strukturierte Daten?


# Aufgaben

##

1. Andere SSGs testen: Jekyll, Hugo
2. Konzept einer Inhaltsstruktur für oer.fh-joanneum.at/contentstrategy entwickeln
    - Welche collections sind interessant?
    - Welche Metadaten sind wichtig?
