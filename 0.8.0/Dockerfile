FROM hashicorp/terraform:0.9.2
MAINTAINER Kazumichi Yamamoto <yamamoto.febc@gmail.com>

LABEL io.whalebrew.config.environment '["SAKURACLOUD_ACCESS_TOKEN", "SAKURACLOUD_ACCESS_TOKEN_SECRET" , "SAKURACLOUD_ZONE" , "SAKURACLOUD_TIMEOUT" , "SAKURACLOUD_TRACE_MODE"]'

ENV TERRAFORM_SAKURACLOUD_VERSION=0.8.0

ADD https://github.com/yamamoto-febc/terraform-provider-sakuracloud/releases/download/v${TERRAFORM_SAKURACLOUD_VERSION}/terraform-provider-sakuracloud_linux-amd64.zip ./
RUN unzip terraform-provider-sakuracloud_linux-amd64.zip -d /bin
RUN rm -f terraform-provider-sakuracloud_linux-amd64.zip

VOLUME ["/workdir"]
WORKDIR /workdir

ENTRYPOINT ["/bin/terraform"]
CMD ["--help"]
