FROM hashicorp/terraform:0.7.0
MAINTAINER Kazumichi Yamamoto <yamamoto.febc@gmail.com>

ENV TERRAFORM_SAKURACLOUD_VERSION=0.4.0

ADD https://github.com/yamamoto-febc/terraform-provider-sakuracloud/releases/download/v${TERRAFORM_SAKURACLOUD_VERSION}/terraform-provider-sakuracloud_linux-amd64.zip ./
RUN unzip terraform-provider-sakuracloud_linux-amd64.zip -d /bin
RUN rm -f terraform-provider-sakuracloud_linux-amd64.zip


VOLUME ["/work"]
WORKDIR /work

ENTRYPOINT ["/bin/terraform"]
CMD ["--help"]
