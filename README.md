# Podcast Feed Generator (Tutorial by Ray Villalobos)
This GitHub Action converts a YAML file into a valid podcast feed, making it easier to manage compared to XML.

# Usage
## Enable Github Pages
1. Navigate to Settings > Pages in your repository.
2. Select the main branch as the source.
3. This will generate a URL for your repository’s content. Take note of this URL for the next step.

## Create a YAML file
Create a YAML file in your repository with the following format:

```
title: <Podcast Title>
subtitle: <Podcast Subtitle>
author: <Author Name>
description: <Podcast Description>
link: <GitHub Pages URL>
image: <Artwork Location>
language: <Podcast Language e.g. en-us>
category: <Postcast Category e.g. Technology https://podcasters.apple.com/support/1691-apple-podcasts-categories>
format: <format of files e.g. audio/mpeg>
item:
  - title: <Podcast Episode Title>
    description: <Podcast Episode Description>
    published: <Date Published - e.g. Thu, 12 Jan 2023 18:00:00 GMT>
    file: <Filename e.g. /audio/TFIT01.mp3>
    duration: <duration e.g. 00:00:36>
    length: <length e.g. 576,324 (Get Info on your files)>
  ... Repeat for each episode
```

## Sample Workflow
You're also going to need your own workflow file. Here's a sample:
```
name: Generate Feed
on: [push]
jobs:
  generate-feed:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repo
        uses: actions/checkout@v3
      - name: Run Feed Generator
        uses: planetoftheweb/podcast-feed-generator@main
```
