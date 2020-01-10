FROM alpine:latest AS repo
RUN apk add --no-cache git

ARG GIT_REVISION
ARG GIT_REPO_URL

RUN set -ex \
  && git clone $GIT_REPO_URL repo -b $GIT_REVISION --depth 1

FROM solr:5.5.5

# TODO: Perform below steps in intermediate container
COPY --from=repo ./solr/config /opt/solr/

WORKDIR /opt/solr/config
# TODO: bash -iex stuff
RUN envsubst < core.properties.envsubst | tee $(ls -d cores/* | sed 's/$/\/core.propeties/') > /dev/null
# TODO: Copy solrconfig or softlink?
RUN 


# REPLACE ENVIRONMENT VARIABLES IN .properties files

# PRECREATE CORE, OR JUST COPY ALL?

# COPY --chown:solr:solr scripts
