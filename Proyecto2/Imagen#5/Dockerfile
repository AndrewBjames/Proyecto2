FROM almalinux:8

RUN dnf -y update && \
    dnf -y install rpm-build createrepo dnf-utils gcc make tar gzip vim \
                   dnf-plugins-core epel-release && \
    dnf clean all && \
    rm -rf /var/cache/dnf

RUN dnf -y config-manager --set-enabled powertools || \
    dnf -y config-manager --set-enabled crb

RUN dnf -y install \
    git curl gcc make bzip2 which \
    autoconf automake bison \
    openssl-devel libyaml-devel libffi-devel \
    readline-devel zlib-devel gdbm-devel ncurses-devel \
    rbenv ruby-build && \
    dnf clean all && rm -rf /var/cache/dnf

RUN dnf -y module enable nodejs:16 && \
    dnf -y install nodejs npm && \
    npm install -g yarn && \
    dnf clean all

RUN dnf -y install python3 python3-pip python3-setuptools && \
    dnf clean all

RUN useradd -m developer
USER developer
WORKDIR /home/developer

RUN echo 'eval "$(rbenv init - bash)"' >> ~/.bashrc

CMD ["bash", "-c", "\
echo '--- Sistema listo ---'; \
echo 'Ruby:'; ruby -v; \
echo 'rbenv:'; rbenv --version; \
echo 'Node.js:'; node -v; \
echo 'npm:'; npm -v; \
echo 'Yarn:'; yarn -v; \
echo 'Python:'; python3 --version; \
echo 'pip:'; pip3 --version; \
echo 'RPM tools listas.' \
"]