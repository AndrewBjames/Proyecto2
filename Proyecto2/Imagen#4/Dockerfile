# Imagen 4 – Python
FROM almalinux:8

# 1) Actualizamos e instalamos Python y herramientas básicas
RUN dnf -y update && \
    dnf -y install python3 python3-pip python3-setuptools && \
    dnf clean all

# 2) Usuario normal
RUN useradd -m developer
USER developer
WORKDIR /home/developer

# 3) Mensaje final simple
CMD ["bash", "-c", "echo 'Python instalado correctamente'; \
echo 'Python:'; python3 --version; \
echo 'pip:'; pip3 --version; \
echo 'venv y setuptools están listos para usarse.'"]
