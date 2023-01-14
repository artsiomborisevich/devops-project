FROM bitnami/drupal

## Change user to perform privileged actions
USER 0
## Install 'vim'
RUN install_packages vim
## Revert to the original non-root user
USER 1001

ENV APP_VERSION=9.5.2