FROM bmeme/gatsby-dev:3.7.1

ARG FIX_UID
ARG FIX_GID

ADD fix-perm.sh /fix-perm.sh
RUN chmod +x /fix-perm.sh && /fix-perm.sh
