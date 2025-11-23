# Imagen 2: AlmaLinux 8 + deps Ruby + rbenv (sin GitHub)
FROM almalinux:8

# 1) Actualizar y habilitar repos necesarios (EPEL + PowerTools/CRB)
RUN dnf -y update
RUN dnf -y install dnf-plugins-core epel-release
# en EL8 se llama "powertools"; en algunas variantes aparece como "crb"
RUN dnf -y config-manager --set-enabled powertools || dnf -y config-manager --set-enabled crb

# 2) Instalar dependencias de compilación de Ruby + rbenv + ruby-build
RUN dnf -y install \
    git curl gcc make bzip2 which \
    autoconf automake bison \
    openssl-devel libyaml-devel libffi-devel \
    readline-devel zlib-devel gdbm-devel ncurses-devel \
    rbenv ruby-build
RUN dnf clean all && rm -rf /var/cache/dnf

# 3) Usuario normal para no trabajar como root
RUN useradd -m developer
USER developer
WORKDIR /home/developer

# 4) Habilitar rbenv al abrir bash
RUN echo 'eval "$(rbenv init - bash)"' >> ~/.bashrc

# 5) Mensaje final simple
CMD ["bash", "-c", "echo 'Ruby y rbenv instalados correctamente'; \
echo 'Ruby:'; ruby -v; \
echo 'rbenv (gestor de versiones):'; rbenv --version;"]
