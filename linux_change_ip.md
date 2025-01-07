# Configurando o IP Local no Ubuntu pelo Terminal

Este guia mostra como configurar o endereço IP local no Ubuntu 24.04 utilizando o terminal, sem a necessidade de editar arquivos manualmente. Usaremos o utilitário `nmcli` para simplificar o processo.

---

## 1. Listar as Interfaces de Rede
Antes de configurar, é necessário identificar o nome da interface de rede.

Use o comando abaixo para listar as interfaces disponíveis:

```bash
ip link show
```

A saída será semelhante a:

```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP mode DEFAULT group default qlen 1000
    link/ether 08:00:27:53:8b:dc brd ff:ff:ff:ff:ff:ff
```

- `lo`: Interface de loopback (ignorar).
- Interface relevante: geralmente `eth0`, `enp0s3` ou outro nome. Verifique qual está ativa.

Para identificar qual interface está conectada à rede, use:

```bash
nmcli device status
```

Saída exemplo:

```
DEVICE      TYPE      STATE      CONNECTION
enp0s3      ethernet  connected  netplan-enp8s0
lo          loopback  unmanaged  --
```

A interface `enp0s3` está conectada e será usada para configuração.

---

## 2. Configurar o Endereço IP
Com o nome da interface identificado, configure o IP local usando o `nmcli`.

Substitua os valores pelos desejados:

```bash
nmcli connection modify "netplan-enp8s0" \
  ipv4.addresses 192.168.1.3/24 \
  ipv4.gateway 192.168.1.254 \
  ipv4.dns "192.168.1.3,8.8.8.8" \
  ipv4.method manual
```

Se a conexão não se chama `netplan-enp8s0`, descubra o nome correto:

```bash
nmcli connection show
```
E substitua o nome no comando acima.

---

## 3. Aplicar as Configurações
Reinicie a conexão para aplicar as novas configurações:

```bash
nmcli connection down "netplan-enp8s0"
nmcli connection up "netplan-enp8s0"
```

---

## 4. Verificar a Configuração
Certifique-se de que o IP foi configurado corretamente:

```bash
nmcli device show enp0s3
```
(Substitua `enp0s3` pelo nome da sua interface.)

Para testar a conectividade, execute:

```bash
ping 192.168.1.254  # Testar o gateway
ping 8.8.8.8        # Testar a internet
```

---

### Observação
O comando `nmcli` permite uma configuração rápida e prática, sem necessidade de editar arquivos de configuração manualmente, garantindo mais agilidade no processo de gerenciamento de redes.
