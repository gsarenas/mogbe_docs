# Debug

- Bugs e inconsistências podem gerar grandes frustrações e perda de tempo. Incluímos uma seção dedicadas a debugging com apontamentos rápidos.

---

| Sintoma: Raspberry Pi ou Dev Machine não consegue clonar repositório `mogbe` |
| --- |
| Solução: Aumente o tamanho do buffer `git` |
| `git config --global http.postBuffer 157286400` |

---

| Sintoma: Não sei qual porta USB Arduino e sensor LiDAR estão conectados |
| --- |
| Solução: Rode os comandos `sudo udevadm info -a -n /dev/ttyUSB0` e `sudo udevadm info -a -n /dev/ttyUSB1` e vasculhe o output |
| `ttyUSB0` deve ser o Arduino: `DRIVERS=="ch341-uart"` enquanto `ttyUSB1` deve ser o LiDAR: `DRIVERS=="cp210x"` |

---