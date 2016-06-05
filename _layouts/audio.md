<?xml version="1.0" encoding="UTF-8"?>
<rss xmlns:itunes="http://www.itunes.com/dtds/podcast-1.0.dtd" version="2.0">
  <channel>
    <title>{{ site.podcast.title }}</title>
    <link>{{ site.podcast.link }}</link>
    <itunes:author>{{ site.author }}</itunes:author>
    <copyright>{{ site.license }}</copyright>
    <language>en-us</language>
    <pubDate>{{ site.time | date_to_rfc822 }}</pubDate>
    <lastBuildDate>{{ site.time | date_to_rfc822 }}</lastBuildDate>
    <itunes:category text="{{ site.podcast.category }}">
      {% for subcategory in site.podcast.subcategories %}
      <itunes:category text="{{ subcategory }}"/>
      {% endfor %}
    </itunes:category>
    <itunes:explicit>No</itunes:explicit>
    <itunes:image href="{{ site.podcast.art }}"/>
    <itunes:subtitle>{{ site.podcast.subtitle }}</itunes:subtitle>
    <description>{{ site.podcast.summary }}</description>
    <itunes:summary>{{ site.podcast.summary }}</itunes:summary>
    <itunes:owner>
      <itunes:name>{{ site.author }}</itunes:name>
      <itunes:email>{{ site.email }}</itunes:email>
    </itunes:owner>

    {% for post in site.categories.podcast %}
    <item>
      <title>{{ post.title }}</title>
      <itunes:explicit>No</itunes:explicit>
      <itunes:author>{{ site.author }}</itunes:author>
      <itunes:duration>{{ post.duration }}</itunes:duration>
      <pubDate>{{ post.date | date_to_rfc822 }}</pubDate>
      <itunes:subtitle>{{post.subtitle}}</itunes:subtitle>
      <itunes:summary><![CDATA[{{ post.content | strip_html }}]]></itunes:summary>
      <description><![CDATA[{{ post.content | strip_newlines }}]]></description>
      <guid isPermaLink="true">{{ post.audio }}</guid>
      <category>{{ site.podcast.category }}</category>
      <enclosure length="{{ post.alength }}" url="{{ post.audio }}" type="audio/mpeg"/>
    </item>
    {% endfor %}
  </channel>
</rss>
