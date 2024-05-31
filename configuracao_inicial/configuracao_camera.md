# (Opcional) Configuração de câmera

## Raspberry Pi

- Para configurar uma câmera, supondo que será usada um módulo de câmera Raspberry Pi versão 1.3 ou 2, instale os drivers (`image-transport-plugins` e `v4l2-camera` já devem ter sido instalados caso tenha feito `rosdep` do MOGBE):

```bash
sudo apt install libraspberrypi-bin \
v4l-utils \
ros-humble-image-transport-plugins \
ros-humble-v4l2-camera
```

- Abra as configurações `raspi-config`:

```bash
sudo raspi-config
```

- `Interface Options` -> `Camera` -> `Yes` para habilitar a interface da câmera.

- `Interface Options` -> `SPI` -> `Yes` para habilitar a interface SPI.

- `Interface Options` -> `I2C` -> `Yes` para habilitar a interface I2C.

- Quando terminal, selecione `Finish` para retornar ao terminal.

- Edite suas configurações de boot:

```bash
sudo nano /boot/firmware/config.txt
```

- Encontre a linha que possui `camera_auto_detect=1` e mude para `camera_auto_detect=0`. Na linha abaixo do novo `display_auto_detect=0`, adicione a linha `start_x=1`.

- Reinicie:

```bash
sudo reboot
```

- Execute o `nó` driver da câmera:

```bash
ros2 run v4l2_camera v4l2_camera_node
```

- Configure a resolução da imagem:

```bash
ros2 param set /v4l2_camera image_size "[240,160]"

```

- Ajuste o brilho da imagem:

```bash
ros2 param set /v4l2_camera brightness "60"
```

```{admonition} Nota
---
class: note
---
Na data de escrita dessa seção da documentação do MOGBE (Maio de 2024), o driver `v4l2_camera` se mostrou relativamente instável em nossos testes com a câmera Raspberry Pi versão 1.3. Por isso, é recomendável executar o `nó` e passar os `parâmetros` de maneira separada ao invés de fazer tudo em um único comando como em `ros2 run v4l2_camera v4l2_camera_node --ros-args -p image_size:="[240,160]" -p camera_frame_id:=camera_optical_link -p brightness:="60"`.
```

---

## Dev Machine

- Instale os drivers (`image-transport-plugins` e `rqt-image-view` já devem ter sido instalados caso tenha feito `rosdep` do MOGBE):

```bash
ros-humble-image-transport-plugins \
ros-humble-rqt-image-view
```

- Com o `nó` driver da câmera rodando no Raspberry Pi, visualize a imagem com:

 ```bash
ros2 run rqt_image_view rqt_image_view 
```

```{admonition} Dica
---
class: tip
---
Com o `nó` da câmera rodando no Raspberry Pi, é possível passar os `parâmetros` pela Dev Machine com `ros2 param set /v4l2_camera brightness "<int>"` e `ros2 param set /v4l2_camera image_size "[<int:largura,int:altura>]"`
```
