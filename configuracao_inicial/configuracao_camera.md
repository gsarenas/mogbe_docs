# (Opcional) Configuração de câmera

## Raspberry Pi

- Para configurar uma câmera, supondo que será usada um módulo de câmera Raspberry Pi, instale os drivers:

```bash
sudo apt install libraspberrypi-bin v4l-utils
```

- Abra as configurações `raspi-config`:

```bash
sudo raspi-config
```

- `Advanced Options` -> `Camera` -> `Yes` para habilitar a interface da câmera.

- `Advanced Options` -> `SPI` -> `Yes` para habilitar a interface SPI.

- `Advanced Options` -> `I2C` -> `Yes` para habilitar a interface I2C.

- Edite suas configurações de boot:

```bash
sudo nano /boot/firmware/config.txt
```

- Encontre a linha que possui `camera_auto_detect=1` e mude para `camera_auto_detect=0`. Na linha abaixo de `display_auto_detect=1`, adicione a linha `start_x=1`.

- Reinicie:

```bash
sudo reboot
```

- Execute o `nó` driver da câmera:

```bash
ros2 run v4l2_camera v4l2_camera_node --ros-args -p image_size:="[240,160]" -p camera_frame_id:=camera_optical_link -p brightness:="60"
```

---

## Dev Machine

- Com o `nó` driver da câmera rodando no Raspberry Pi, visualize a imagem com:

 ```bash
ros2 run rqt_image_view rqt_image_view 
```
