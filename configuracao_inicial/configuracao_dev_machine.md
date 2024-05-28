# Configuração de OS: Dev Machine

## Ubuntu Desktop 22.04.4 LTS

```{admonition} Nota
---
class: note
---
O projeto foi desenvolvido e implementado utilizando uma máquina virtual (guest machine) rodando Ubuntu 64-bit através do VMware Workstation 17 Player em uma host machine rodando Windows 11. A máquina virtual foi configurada utilizando definições padrão: 4 GB de memória RAM, 2 processadores, etc.
```

- Certifique-se de que esteja rodando [Ubuntu Desktop versão Jammy Jellyfish 22.04.4 LTS](https://releases.ubuntu.com/jammy/).

---

## ROS 2 Humble

- Instale o ROS 2 versão Humble Hawksbill seguindo o [tutorial](https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debians.html) da documentação oficial. Prossiga até instalar `ros-humble-desktop` e `ros-dev-tools`, não é necessário instalar `ros-humble-base` para a dev machine.

```{admonition} Nota
---
class: note
---
Para evitar a necessidade de utilizar o comando `source /opt/ros/humble/setup.bash` toda vez que rodar uma aplicação ROS 2, configure as variáveis de ambiente do diretório de instalação de ROS 2 em seu arquivo `~/.bashrc`:
```

```bash
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
```

- Em um novo terminal, verifique se as variáveis de ambiente foram configuradas corretamente:

```bash
printenv | grep -i ROS
```

- Você deve encontrar informações na saída do terminal como:

```bash
ROS_VERSION=2
ROS_PYTHON_VERSION=3
ROS_DISTRO=humble
```

- Para testar a instalação, abra um terminal e rode o exemplo de `talker` em C++:

```bash
ros2 run demo_nodes_cpp talker
```

- Abra um novo terminal e rode o exemplo de `listener` em Python:

```bash
ros2 run demo_nodes_py listener
```

- Nesse exemplo, espera-se ver o `talker` publicando suas mensagens e o `listener` reproduzindo o que foi publicado.
