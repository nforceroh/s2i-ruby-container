FROM registry.access.redhat.com/ubi8/ruby-30

ENV JEKYLL_VERSION="4.2.2" \
    SUMMARY="Jekyll ${JEKYLL_VERSION}" \
    DESCRIPTION="Platform for building static jekyll sites (ubi8)"

LABEL maintainer="Gerd Hoffmann <kraxel@redhat.com>" \
      summary="${SUMMARY}" \
      description="${DESCRIPTION}" \
      io.k8s.display-name="${SUMMARY}" \
      io.k8s.description="${DESCRIPTION}" \
      io.openshift.expose-services="8080:http" \
      io.openshift.tags="jekyll,static" \
      io.openshift.s2i.scripts-url="image:///usr/libexec/s2i"

USER root

COPY ./s2i/bin/ /usr/libexec/s2i

RUN set -x; \
    gem install puma Rack Bundler \
    gem install jekyll --version "= $JEKYLL_VERSION"

USER 1001
EXPOSE 8080

CMD ["/usr/libexec/s2i/usage"]