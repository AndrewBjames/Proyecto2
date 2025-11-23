# Imagen 3 – Node.js y Yarn
FROM almalinux:8

# 1) Actualizamos e instalamos Node.js y Yarn desde los repositorios oficiales
RUN dnf -y update && \
    dnf -y module enable nodejs:16 && \
    dnf -y install nodejs npm && \
    npm install -g yarn && \
    dnf clean all

# 2) Creamos un usuario normal
RUN useradd -m developer
USER developer
WORKDIR /home/developer

# 3) Mensaje final simple
CMD ["bash", "-c", "echo 'Node.js y Yarn instalados correctamente'; \
echo 'Node.js:'; node -v; \
echo 'npm:'; npm -v; \
echo 'Yarn (gestor de paquetes):'; yarn -v;"]
