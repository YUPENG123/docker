# ab (apache benchmark)
# in a container
#
# docker run --rm -it \
# 	jess/ab
#
FROM alpine@sha256:25109184c71bdad752c8312a8623239686a9a2071e8825f20acb8f2198c3f659
LABEL maintainer "Jessie Frazelle <jess@linux.com>"

RUN apk --no-cache add \
	apache2-ssl \
	apache2-utils \
	ca-certificates \
	htop

ENTRYPOINT [ "ab" ]
