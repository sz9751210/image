FROM --platform=linux/amd64 amazon/aws-cli:2.4.9

# Define environment variables for versions
ENV KUBECTL_VERSION="v1.28.0" \
    TERRAFORM_VERSION="1.6.5"

# Install additional dependencies
RUN yum install -y \
        gettext \
        unzip \
        groff \
        less \
    && yum clean all

# Install kubectl
RUN curl -LO "https://dl.k8s.io/release/${KUBECTL_VERSION}/bin/linux/amd64/kubectl" \
    && chmod +x kubectl \
    && mv kubectl /usr/local/bin

# Install Terraform
RUN curl -LO "https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip" \
    && unzip terraform_${TERRAFORM_VERSION}_linux_amd64.zip \
    && chmod +x terraform \
    && mv terraform /usr/local/bin

# Setting up working directory
WORKDIR /workspace

# The entrypoint is the shell
ENTRYPOINT ["/bin/bash"]
