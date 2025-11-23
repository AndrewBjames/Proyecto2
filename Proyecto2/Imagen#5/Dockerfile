# Imagen 5 – FULL (RPM + Ruby/rbenv + Node/Yarn + Python)
FROM almalinux:8

# 1) Actualizar y habilitar repos necesarios
RUN dnf -y update
RUN dnf -y install epel-release dnf-plugins-core
RUN dnf -y config-manager --set-enabled powertools || dnf -y config-manager --set-enabled crb

# 2) Herramientas RPM
RUN dnf -y install rpm-build createrepo dnf-utils gcc make tar gzip bzip2 vim

# 3) Ruby: dependencias + rbenv (desde repos)
RUN dnf -y install git curl which \
                   rbenv ruby-build \
                   openssl-devel libyaml-devel libffi-devel \
                   readline-devel zlib-devel gdbm-devel ncurses-devel

# 4) Node.js 16 + npm + Yarn (simple, desde repos)
RUN dnf -y module enable nodejs:16
RUN dnf -y install nodejs npm
RUN npm install -g yarn

# 5) Python 3.x + pip + setuptools
RUN dnf -y install python3 python3-pip python3-setuptools

# 6) Limpieza
RUN dnf clean all

# 7) Usuario normal
RUN useradd -m developer
USER developer
WORKDIR /home/developer

# 8) Mensaje de verificación sencillo
CMD ["bash","-c","echo 'Entorno FULL listo'; \
echo 'RPM:'; rpm --version; \
echo 'rbenv:'; rbenv --version || echo 'rbenv instalado'; \
echo 'Node:'; node -v; \
echo 'Yarn:'; yarn -v; \
echo 'Python:'; python3 --version; \
echo 'pip:'; pip3 --version"]
