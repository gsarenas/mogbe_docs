# Cola Rápida

Aqui temos uma "cola rápida" dos comandos que estão por trás do arquivos `.launch.py` caso necessite inicializar os processos de maneira separada. Há também alguns comandos adicionais de ferramentas e recursos (ROS e terceiros) que permitem melhor entendimento e/ou visualização do funcionamento do MOGBE. Caso queira explorá-los, reserve um tempo para estudá-los com calma, pois alguns possuem sequência e dependem de outros processos para funcionarem.

```{admonition} Dica
---
class: tip
---
Entenda valores entre `<` `>` como o tipo de dado esperado para os parâmetros. Exemplo: `use_sim_time:=<bool>` &#8594; `use_sim_time:=true` | `use_sim_time:=false`.
```

| Descrição | Ambiente | Comando|
| :-------: | :------: | :----: | 
| Robô (real) | Pi | `ros2 launch mogbe launch_robot.launch.py` |
| LiDAR | Pi | `ros2 launch ldlidar_stl_ros2 ld19.launch.py` |
| Robô (sim) + controlador + mundo + posição | Dev | `ros2 launch mogbe launch_sim.launch.py use_ros2_control:=<bool> world:=./src/mogbe/worlds/<world_name.world> x:=<float> y:=<float> z:=<float>` |
| teleop_twist_keyboard | Dev/Pi | `ros2 run teleop_twist_keyboard teleop_twist_keyboard --ros-args -r /cmd_vel:=</cmd_vel_joy>` |
| twist_mux | Dev/Pi | `ros2 run twist_mux twist_mux --ros-args --params-file ./src/mogbe/config/twist_mux.yaml -r cmd_vel_out:=diff_cont/cmd_vel_unstamped` |
| slam_toolbox (mapping) | Dev | `ros2 launch mogbe online_async_launch.py use_sim_time:=<bool>` |
| slam_toolbox (localization) | Dev | `ros2 launch mogbe localization_launch.py use_sim_time:=<bool>` |
| Navigation2 | Dev | `ros2 launch mogbe navigation_launch.py use_sim_time:=<bool>` |
| gazebo_ros + mundo específico| Dev | `ros2 launch gazebo_ros gazebo.launch.py extra_gazebo_args:="--ros-args --params-file ./src/mogbe/config/gazebo_params.yaml" world:=</path/to/world_name.world>` |
| robot_state_publisher | Dev/Pi | `ros2 launch mogbe rsp.launch.py use_sim_time:=<bool> use_ros2_control:=<bool>` |
| gazebo_ros + spawn_entity + posição | Dev | `ros2 run gazebo_ros spawn_entity.py -topic robot_description -entity <robot_name> -x <float> -y <float> -z <float>` |
| Carrega e ativa diff_drive_controller/DiffDriveController | Dev/Pi | `ros2 run controller_manager spawner diff_cont` |
| Carrega e ativa joint_state_broadcaster/JointStateBroadcaster | Dev/Pi | `ros2 run controller_manager spawner joint_broad`
| Publica mensagem cmd_vel | Dev/Pi | `ros2 topic pub /diff_cont/cmd_vel_unstamped geometry_msgs/msg/Twist '{linear: {x: <float>, y: 0.0, z: 0.0}, angular: {x: 0.0, y: 0.0, z: <float>}}' --rate 30` |
| Verifica msg LiDAR | Dev/Pi | `ros2 topic echo /scan` |
| Verifica estado das juntas | Dev/Pi | `ros2 topic echo /joint_states` |
| Lista interfaces de hardware | Dev/Pi | `ros2 control list_hardware_interfaces` |
| Lista componentes de hardware | Dev/Pi | `ros2 control list_hardware_components` |
| Lista controladores | Dev/Pi | `ros2 control list_controllers` |
| RQt | Dev | `rqt` |
| rqt_graph | Dev | `ros2 run rqt_graph rqt_graph` |
| tf2 árvore hierárquica (PDF) | Dev | `ros2 run tf2_tools view_frames` |
| tf2 transformada entre dois frames | Dev/Pi | `ros2 run tf2_tools tf2_echo <frame_1> <frame_2>` |
| RViz + config específica| Dev | `rviz2` |
| Gazebo + mundo específico | Dev | `gazebo </path/to/world_name.world>` |
| PlotJuggler (instalação) | Dev | `sudo snap install plotjuggler` |
| PlotJuggler (gráficos em tempo real) | Dev | `plotjuggler` |