# Rodando o robô físico

## Raspberry Pi

- Garanta que esteja na pasta `mogbe_ws` e que as variáveis de ambiente estejam configuradas:

```bash
cd ~/mogbe_ws && source install/setup.bash
```

- Inicie o robô e sensor lidar:

```bash
ros2 launch mogbe launch_robot_pi_all.launch.py
```

## Dev Machine

- Após ter inicializado o MOGBE no Raspberry Pi, abra um novo terminal, garanta que esteja na pasta de trabalho `mogbe_ws` e que as variáveis de ambiente estejam configuradas:

```bash
cd ~/mogbe_ws && source install/setup.bash
```

- Execute os `nós` de SLAM, navegação autônoma e visualização:

```bash
ros2 launch mogbe launch_robot_dev.launch.py
```

- Para controle manual do MOGBE, é necessário abrir uma nova aba de terminal e executar o `nó` de comando `teleop`:

```bash
ros2 run teleop_twist_keyboard teleop_twist_keyboard --ros-args -r /cmd_vel:=/cmd_vel_joy
```

```{admonition} Dica
---
class: tip
---
É necessário que o terminal com o `teleop_twist_keyboard` esteja em foco para controlar o robô manualmente.
```