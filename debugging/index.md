# Debug

- Bugs e inconsistências podem gerar grandes frustrações e perda de tempo. Incluímos uma seção dedicada a debugging com alguns apontamentos rápidos.

---

**Sintoma:** Raspberry Pi ou Dev Machine não consegue clonar repositório `mogbe`

**Solução:** Aumente o tamanho do buffer `git`

```bash
git config --global http.postBuffer 157286400
```

---

**Sintoma:** Não sei qual porta USB Arduino e sensor LiDAR estão conectados

**Solução:** Rode os comandos `sudo udevadm info -a -n /dev/ttyUSB0` e `sudo udevadm info -a -n /dev/ttyUSB1` e vasculhe o output

`ttyUSB0` deve ser o Arduino: `DRIVERS=="ch341-uart"` enquanto `ttyUSB1` deve ser o LiDAR: `DRIVERS=="cp210x"`

---

**Sintoma:** Não consigo instalar as dependências com `rosdep`

**Solução:** Alguns releases podem deixar de funcionar com `rosdep`. Nesse caso, é possível instalar as dependências manualmente:

Dev Machine:

```bash
sudo apt install ros-humble-gazebo-ros-pkgs \
ros-humble-ros2-control \
ros-humble-ros2-controllers \
ros-humble-gazebo-ros2-control \
ros-humble-slam-toolbox \
ros-humble-navigation2 \
ros-humble-nav2-bringup \
ros-humble-twist-mux \
ros-humble-xacro \
ros-humble-image-transport-plugins \
ros-humble-rqt-image-view
```

Pi:

```bash
sudo apt install ros-humble-demo-nodes-cpp \
ros-humble-demo-nodes-py \
ros-humble-ros2-control \
ros-humble-ros2-controllers \
ros-humble-slam-toolbox \
ros-humble-navigation2 \
ros-humble-nav2-bringup \
ros-humble-twist-mux \
ros-humble-xacro \
ros-humble-image-transport-plugins \
ros-humble-v4l2-camera
```
