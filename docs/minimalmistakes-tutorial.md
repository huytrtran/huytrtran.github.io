# Guide to creating a GitHub pages website with the Minimal Mistakes theme

## Table of Contents
1. [Creating the website](#creating)
1. [Updating the website](#updating-the-website)

<a name="creating"></a>
## Creating the website

The following steps detail how to create a GitHub pages website using the [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/) Jekyll theme. The steps in Option 1 are based on [this guide](http://varianceexplained.org/theme-setup/). The Minimal Mistakes guide suggests that installing as a remote theme (Option 2) is ["ideal for sites hosted with GitHub Pages"](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/#remote-theme-method). More details can be found in the Minimal Mistakes [Quick-Start Guide](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/) and [Installation](https://mmistakes.github.io/minimal-mistakes/docs/installation/) instructions.

The [GitHub pages website](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll) also provides a nice tutorial for setting up a pages with Jekyll.

### Option 1: Forking the theme (untested).

Make sure to replace < username > with your GitHub username.

1. [Fork](http://github.com/mmistakes/minimal-mistakes/fork) the Minimal Mistakes repo to your GitHub account. Rename the repo to your GitHub username.

1. Clone the repo to your local machine to enable local edits.

        $ cd Documents/sites
        $ git clone https://github.com/username/username.git

1. Remove the following unnecessary files and directories from your local repo.

  - .editorconfig
  - .gitattributes
  - .github
  - /docs
  - /test
  - CHANGELOG.md
  - minimal-mistakes-jekyll.gemspec
  - README.md
  - screenshot-layouts.png
  - screenshot.png

1. Replace your Gemfile with the following and save. The "jekyll-remote-theme" Gem enables [hosting](https://github.com/benbalter/jekyll-remote-theme) with GitHub pages.

        source "https://rubygems.org"

        # Hello! This is where you manage which Jekyll version is used to run.
        # When you want to use a different version, change it below, save the
        # file and run `bundle install`. Run Jekyll with `bundle exec`, like so:
        #
        #     bundle exec jekyll serve
        #
        # This will help ensure the proper Jekyll version is running.
        # Happy Jekylling!

        gem "github-pages", group: :jekyll_plugins

        # To upgrade, run `bundle update`.

        # gem "jekyll"
        gem "minimal-mistakes-jekyll"

        # The following plugins are automatically loaded by the theme-gem:
        #   gem "jekyll-paginate"
        #   gem "jekyll-sitemap"
        #   gem "jekyll-gist"
        #   gem "jekyll-feed"
        #   gem "jemoji"
        #   gem "jekyll-data"
        #   gem "jekyll-include-cache"
        #
        # If you have any other plugins, put them here!
        group :jekyll_plugins do
        end

1. Run the following to locally test and spin up your site! You can view your site by browsing to http://localhost:4000. The GitHub Pages documentation has more details on [testing locally with Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/testing-your-github-pages-site-locally-with-jekyll).

        $ bundle exec jekyll serve

    Note that if you are using Ruby version 3.0.0 or higher, the `bundle exec jekyll serve` command may fail. You may fix it by adding webrick to your dependencies.

        $ bundle add webrick

### Option 2: Installing as a Remote Theme and starting fresh (untested).

These steps only provide a base local site from which you can build your site.

1. Install Jekyll following the steps [here](https://jekyllrb.com/docs/installation/) (e.g., [here](https://jekyllrb.com/docs/installation/macos/) for macOS). These steps will install Ruby, Bundler, and Jekyll. I would suggest a local install.

1. Create a new directory for your website's files (replacing username with your GitHub username), create an empty `Gemfile` file, create an empty `_config.yml` file, and open the `Gemfile` and `_config.yml` files for editing.

        $ cd Documents/sites
        $ mkdir <username>
        $ cd <username>/
        $ touch Gemfile
        $ touch _config.yml
        $ open Gemfile
        $ open _config.yml

1. Insert the following into your Gemfile and save. The "jekyll-remote-theme" Gem enables [hosting](https://github.com/benbalter/jekyll-remote-theme) with GitHub pages.

        source "https://rubygems.org"

        # Hello! This is where you manage which Jekyll version is used to run.
        # When you want to use a different version, change it below, save the
        # file and run `bundle install`. Run Jekyll with `bundle exec`, like so:
        #
        #     bundle exec jekyll serve
        #
        # This will help ensure the proper Jekyll version is running.
        # Happy Jekylling!

        gem "github-pages", group: :jekyll_plugins
        gem "jekyll-remote-theme"
        gem "jekyll-include-cache"

        # To upgrade, run `bundle update`.

1. Copy the contents of the default `_config.yml` file from [here](https://github.com/mmistakes/minimal-mistakes/blob/master/_config.yml) into your `_config.yml` file and save. Make sure that "jekyll-include-cache" is included in the "plugins" array of your `_config.yml` file.

1. Fetch and update bundled gems by running the following.

        $ bundle

1. Add the Minimal Mistakes remote theme to your `_config.yml` by including the following line in the "theme" section of your `_config.yml` (this line may already exist and be commented out). Remove any other theme or remote_theme.

        remote_theme             : "mmistakes/minimal-mistakes"

1. Run the following to locally test and spin up your site! You can view your site by browsing to http://localhost:4000. The GitHub Pages documentation has more details on [testing locally with Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/testing-your-github-pages-site-locally-with-jekyll).

        $ bundle exec jekyll serve

    Note that if you are using Ruby version 3.0.0 or higher, the `bundle exec jekyll serve` command may fail. You may fix it by adding webrick to your dependencies.

        $ bundle add webrick

### Option 3: Installing as a Remote Theme using the Minimal Mistakes remote theme starter.

These steps only provide a base local site from which you can build your site.

1. Install Jekyll following the steps [here](https://jekyllrb.com/docs/installation/) (e.g., [here](https://jekyllrb.com/docs/installation/macos/) for macOS). These steps will install Ruby, Bundler, and Jekyll. I would suggest a local install.

1. Use the repo template found [here](https://github.com/mmistakes/mm-github-pages-starter). Then replace sample content with your own and [configure as necessary](https://mmistakes.github.io/minimal-mistakes/docs/configuration/). An example `_config.yml` file can be found [here](https://github.com/mmistakes/minimal-mistakes/blob/master/_config.yml).

1. Run the following to locally test and spin up your site! You can view your site by browsing to http://localhost:4000. The GitHub Pages documentation has more details on [testing locally with Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/testing-your-github-pages-site-locally-with-jekyll).

        $ bundle exec jekyll serve

    Note that if you are using Ruby version 3.0.0 or higher, the `bundle exec jekyll serve` command may fail. You may fix it by adding webrick to your dependencies.

        $ bundle add webrick

<a name="updating"></a>
## Updating the website

Run the following to locally test and spin up your site! You can view your site by browsing to http://localhost:4000. The GitHub Pages documentation has more details on [testing locally with Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/testing-your-github-pages-site-locally-with-jekyll).

        $ bundle exec jekyll serve

    Note that if you are using Ruby version 3.0.0 or higher, the `bundle exec jekyll serve` command may fail. You may fix it by adding webrick to your dependencies.

        $ bundle add webrick