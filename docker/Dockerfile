# Multi-stage
# 1) Jekyll image for building static blog site
# 2) nginx stage to serve static site

FROM ruby:3.4.2 AS builder

WORKDIR /srv/jekyll

COPY . .

RUN gem install bundler
RUN bundle install
RUN jekyll build --trace

# 2) Nginx stage for serving content

FROM nginx

# Set our working directory inside the image
WORKDIR /var/www/public

COPY --from=builder /srv/jekyll/_site .

# Copy Nginx config template
COPY docker/nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 443

ENTRYPOINT ["nginx", "-g", "daemon off;"]
