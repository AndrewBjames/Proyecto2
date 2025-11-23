# Imagen base de AlmaLinux 8
FROM almalinux:8

# Actualizamos el sistema y agregamos herramientas de RPM
RUN dnf -y update && \
    dnf -y install rpm-build createrepo dnf-utils gcc make tar gzip vim && \
    dnf clean all && \
    rm -rf /var/cache/dnf

# Creamos un usuario normal para no trabajar como root
RUN useradd -m packager
USER packager
WORKDIR /home/packager

# Mensaje final simple
CMD ["bash", "-c", "echo 'Herramientas RPM listas para usar'; \
echo 'Versión de RPM:'; rpm --version;"]



