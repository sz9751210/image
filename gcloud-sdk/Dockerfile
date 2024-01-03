FROM --platform=linux/amd64 python:3-alpine

RUN apk update && \
    apk add yq gettext bash git curl make
RUN export GCLOUD_SDK=google-cloud-cli-420.0.0-linux-x86_64.tar.gz && \
    wget https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/$GCLOUD_SDK && \
    tar -xf $GCLOUD_SDK && \
    rm -f $GCLOUD_SDK && \
    ./google-cloud-sdk/install.sh --quiet && \
    ln -s $(pwd)/google-cloud-sdk/bin/gcloud /bin

# install kubectl.
RUN gcloud components install kubectl --quiet
RUN ln -s $(pwd)/google-cloud-sdk/bin/kubectl /bin
