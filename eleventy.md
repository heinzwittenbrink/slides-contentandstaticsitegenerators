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

##

> You want this, so that non-technical folks are also able to create content for static site generators.
> You want this, so that you can use static site generators in many more customer projects.
> You want this, so that no developer is required to update the repository and run the site.

Contentful: [CMS-functionality for static site generators](https://www.contentful.com/r/knowledgebase/contentful-api-cms-static-site-generators/)

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

##

Contentful

> offers webhooks that you can use to rebuild your static site in a fully automated fashion every time your content is modified.

Contentful: [CMS-functionality for static site generators](https://www.contentful.com/r/knowledgebase/contentful-api-cms-static-site-generators/)


## Building und Deploying Sites/Apps

> On your host: Create a webhook endpoint that starts a new build and deploys a project whenever it receives a POST request.

> On Contentful: Create a webhook with the host endpoint as destination URL.

Contentful: [CMS-functionality for static site generators](https://www.contentful.com/r/knowledgebase/contentful-api-cms-static-site-generators/)

## Staging

> deploying to a separate domain that is only known to your editors will give them the chance to preview if the site is exactly looking like they want it to.

Contentful: [CMS-functionality for static site generators](https://www.contentful.com/r/knowledgebase/contentful-api-cms-static-site-generators/)

## Tools


- Plugins für Middleman, Jekyll, Gatsby, Metalsmith
- Nicht offiziell supportete Plugins für Roots und AWS Lambda
- Nicht offizieller Simple Static Site Generator (*A CLI tool to generate a site from templates and data in a Contentful space*)

## Exportieren

[Importing and exporting content with the Contentful CLI – Contentful](https://www.contentful.com/developers/docs/tutorials/cli/import-and-export/)


## Beispielprojekt Contentful und Hugo

- [contentful-hugo](https://www.npmjs.com/package/contentful-hugo)
- Bei diesem Projekt kann man sehen, wie die contentful Dateien in die Hugo Struktur, also eine Struktur von markdown Dateien übersetzt wird.

##

> This is a simple Node.js CLI tool that pulls data from Contentful CMS and turns it into Markdown or YAML files for use with a static site generator. It can be used with any static site generator that uses Markdown with YAML frontmatter, but it has some features that are specific to Hugo.

##

> In this example when you run npm start it will first use contentful-hugo to pull Contentful data then start hugo server. In the same way when you do the command npm run build it will first use contentful-hugo to pull Contentful data then run hugo --minify to build a minified version of your hugo site.

##

> Files will be generated in the directory specified in the contentful-settings.yaml file. Front matter will be in YAML format. Files of single types will be named after fileName specified in the config file. Files of repeatable types will be named after their entry ID in Contenful, which makes it easy to link files together.

## JSON für Rich Text

> A Rich text field will produce nested arrays mirroring the JSON structure that they have in the API. Each node will need to be looped through and produce HTML depending on the nodeType field.

##

> In addition a plaintext version of the field will be generated using the field ID appended with "_plaintext". This allows you to quickly fetch the text by itself without any of the other data. A simple use case would be using the plaintext output to automatically generate a meta description for a webpage.


# Fragen

## Unterstützen SSGs das Prinzip *Content First* besser als andere CMS?

## Welchen Support bieten sie für strukturierte Daten?


# Aufgaben

##

1. Andere SSGs testen: Jekyll, Hugo
2. Konzept einer Inhaltsstruktur für oer.fh-joanneum.at/contentstrategy entwickeln
    - Welche collections sind interessant?
    - Welche Metadaten sind wichtig?
