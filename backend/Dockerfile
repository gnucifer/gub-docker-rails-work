FROM ruby:2.3.1

ARG GIT_REVISION
ARG GIT_REPO_URL

RUN apt-get update \
  && apt-get install -y --no-install-recommends \
    postgresql-client \
    git \
  && rm -rf /var/lib/apt/lists/*

WORKDIR /usr/src/app

RUN set -ex \
  && git clone $GIT_REPO_URL repo -b $GIT_REVISION --depth 1

WORKDIR /usr/src/app/repo
RUN bundle install

EXPOSE 3000
CMD ["sh", "-c", "rails server -b 0.0.0.0 -e $GUP_ENVIRONMENT"]
