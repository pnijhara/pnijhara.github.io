---
title: "Build Static Pages With Hugo by Github Actions"
date: 2021-05-22T20:08:25+05:30
categories:
- blog
- Random discovery
tags:
- hugo blog
- create blog
- go programming language
keywords:
- tech
autoThumbnailImage : false
---
It's been more than 2 years since I have written a blog (actually 2) on [how to create a blogging website with Hugo](https://pnijhara.github.io/2019/08/create-your-own-blog-in-30-minutes-using-hugo-a-static-site-generator-written-in-go/). The blog followed [official documentation](https://gohugo.io/documentation/) but in simple words. [The second blog](https://pnijhara.github.io/2019/08/uncovered-points-associated-with-hugo/) on the same topic was focussing on the problems that went uncovered in the documentation.

In the first blog, I have written a step on how to build the static pages with hugo. Its command was also very simple:
```shell
hugo -d ../example.github.io/
```

The above command builds the static pages in the `example.github.io` directory.

But there is a problem associated with this type of use case. I was using this approach of writing blogs and publishing. I was doing a repetitive task of cloning my blog(Hugo project repo) and the pnijhara.gihub.io(static pages repo). And I was pushing both the repositories separately on GitHub after making changes.

While working with the [amu-oss website](https://amu-oss.github.io) and after reading [RJ722's comment](https://github.com/amu-oss/amu-oss.github.io/pull/3#issuecomment-844102339), I came to know that I was doing this all wrong. This whole process can be automated by GitHub actions, where I have to just push the push the Hugo project to the `master` branch and GitHub action will automatically build the static pages out of it in the `gh-pages` branch.

Let us give it a look.

1. Make a new `gh-pages` branch
2. Ask GitHub to build this branch by going into the settings tab of your repo
3. Visit the GitHub actions tab of your repo
4. Add a new workflow
5. Copy the following content

```yml
name: Build site

on:
  push:
    branches:
      - master  # Set a branch to deploy

jobs:
  deploy:
    runs-on: ubuntu-18.04
    steps:
      - uses: actions/checkout@v2
        with:
          submodules: true  # Fetch Hugo themes (true OR recursive)
          fetch-depth: 0    # Fetch all history for .GitInfo and .Lastmod

      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v2
        with:
          hugo-version: 'latest'

      - name: Build
        run: hugo --minify

      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./public
```

5. Name the file (name doesn't matter, I have named it build-site.yml)
6. Commit the changes

And it's done. From now on you just have to push your Hugo project to GitHub and the rest will be taken care of by [GitHub acitons](https://github.com/pnijhara/pnijhara.github.io/actions).

Read my other blogs on Hugo:
1. https://pnijhara.github.io/2019/08/create-your-own-blog-in-30-minutes-using-hugo-a-static-site-generator-written-in-go/
2. https://pnijhara.github.io/2019/08/uncovered-points-associated-with-hugo/
3. https://pnijhara.github.io/2021/05/install-chocolatey-on-windows/
