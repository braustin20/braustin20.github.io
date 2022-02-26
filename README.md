# braustin.dev

Portfolio site built using Jekyll and [TeXt Theme](https://github.com/kitian616/jekyll-TeXt-theme).

Hosted on GitHub Pages

## Local Development
- Install Docker Desktop

- Run the bundler to set up dependencies
  - `bundle install --path vendor/bundle`
- Generate the Gemfile.lock
  - `docker run --rm -v ${pwd}:/usr/src/app -w /usr/src/app ruby:2.7 bundle install`
- Build docker image
  - `docker-compose -f ./docker/docker-compose.build-image.yml build`
- Run docker image
  - `docker-compose -f ./docker/docker-compose.default.yml up`
