FROM quay.io/devfile/universal-developer-image:ubi8-latest

USER 0
# Install any dependencies
RUN \
  cp -v /run/secrets/kubernetes.io/serviceaccount/ca.crt /etc/pki/ca-trust/source/anchors/  && \
  update-ca-trust && \
  curl http://cli-server.trusted-artifact-signer.svc.cluster.local:8080/clients/linux/cosign-amd64.gz | gunzip | dd of=/usr/local/bin/cosign && \
  curl http://cli-server.trusted-artifact-signer.svc.cluster.local:8080/clients/linux/gitsign-amd64.gz | gunzip | dd of=/usr/local/bin/gitsign && \
  chmod -v +x /usr/local/bin/*

USER 10001

# Specify the command to run on container start
CMD [ "/bin/bash" ]
