# Exemplos

## Rodando uma simulação

- Simulações são executadas na dev machine e independem do Raspberry Pi. Para executar um exemplo, garanta que esteja na pasta `mogbe_ws` e que as variáveis de ambiente estejam configuradas:

```bash
cd ~/mogbe_ws && source install/setup.bash
```

- Execute a simulação de teste no ambiente `wall.world`:

```bash
ros2 launch mogbe launch_sim_all.launch.py world:=./src/mogbe/worlds/wall.world
```

- O ambiente de simulação Gazebo, a ferramenta de visualização RViz e demais `nós` devem inicializar. Lembre-se que o Gazebo é o simulador 3D, enquanto o RViz como o robô "enxerga" o mundo com as informações limitadas que tem.

![gazebo_rviz_sim_small](img/gazebo_rviz_sim_small.png)

- Para controle manual do robô na simulação, abra um novo terminal e rode o `nó` de comando `teleop_twist_keyboard`:

```bash
ros2 run teleop_twist_keyboard teleop_twist_keyboard --ros-args -r /cmd_vel:=/cmd_vel_joy
```

> [!TIP]
> É necessário que o terminal com o `teleop_twist_keyboard` esteja em foco para controlar o robô manualmente.

## Rodando o robô físico

### Raspberry Pi

- Garanta que esteja na pasta `mogbe_ws` e que as variáveis de ambiente estejam configuradas:

```bash
cd ~/mogbe_ws && source install/setup.bash
```

- Inicie o robô e sensor lidar:

```bash
ros2 launch mogbe launch_robot_pi_all.launch.py
```

### Dev Machine

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

> [!TIP]
> É necessário que o terminal com o `teleop_twist_keyboard` esteja em foco para controlar o robô manualmente.