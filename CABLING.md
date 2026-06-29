# Cabling map — match GNS3 to these exactly

## HQ inside (full mesh, transit VLAN 100)

| From          | To            |
| ------------- | ------------- |
| DS-HQ1 G0/0   | FW-HQ1 Port2  |
| DS-HQ1 G0/1   | FW-HQ2 Port2  |
| DS-HQ2 G0/0   | FW-HQ2 Port3  |
| DS-HQ2 G0/1   | FW-HQ1 Port3  |
| DS-HQ1 G3/0   | DS-HQ2 G3/0   |
| DS-HQ1 G3/1   | DS-HQ2 G3/1   |
| DS-HQ1 G0/2   | AS-HQ1 G0/0   |
| DS-HQ1 G0/3   | AS-HQ2 G0/0   |
| DS-HQ2 G0/2   | AS-HQ2 G0/1   |
| DS-HQ2 G0/3   | AS-HQ1 G0/1   |
| FW-HQ1 Port10 | FW-HQ2 Port10 |

## HQ WAN (each FW member to BOTH wan switches)

| From             | To               |
| ---------------- | ---------------- |
| FW-HQ1 Port4     | ISP-A-SW-HQ G0/0 |
| FW-HQ2 Port4     | ISP-A-SW-HQ G0/1 |
| ISP-A-SW-HQ G0/2 | ISP-A-HQ G0/2    |
| FW-HQ1 Port5     | ISP-B-SW-HQ G0/0 |
| FW-HQ2 Port5     | ISP-B-SW-HQ G0/1 |
| ISP-B-SW-HQ G0/2 | ISP-B-HQ G0/2    |
| ISP-A-HQ G0/0    | Internet G0/0    |
| ISP-B-HQ G0/0    | Internet G0/1    |

## BR inside (full mesh, transit VLAN 200)

| From          | To            |
| ------------- | ------------- |
| DS-BR1 G0/0   | FW-BR1 Port2  |
| DS-BR1 G0/1   | FW-BR2 Port2  |
| DS-BR2 G0/0   | FW-BR2 Port3  |
| DS-BR2 G0/1   | FW-BR1 Port3  |
| DS-BR1 G3/0   | DS-BR2 G3/0   |
| DS-BR1 G3/1   | DS-BR2 G3/1   |
| DS-BR1 G0/2   | AS-BR1 G0/0   |
| DS-BR1 G0/3   | AS-BR2 G0/0   |
| DS-BR2 G0/2   | AS-BR1 G0/1   |
| DS-BR2 G0/3   | AS-BR2 G0/1   |
| FW-BR1 Port10 | FW-BR2 Port10 |

## BR WAN

| From             | To               |
| ---------------- | ---------------- |
| FW-BR1 Port4     | ISP-A-SW-BR G0/0 |
| FW-BR2 Port4     | ISP-A-SW-BR G0/1 |
| ISP-A-SW-BR G0/2 | ISP-A-BR G0/2    |
| FW-BR1 Port5     | ISP-B-SW-BR G0/0 |
| FW-BR2 Port5     | ISP-B-SW-BR G0/1 |
| ISP-B-SW-BR G0/2 | ISP-B-BR G0/2    |
| ISP-A-BR G0/0    | Internet G0/2    |
| ISP-B-BR G0/0    | Internet G0/3    |

## Internet core + NAT

| From          | To             |
| ------------- | -------------- |
| Internet G1/0 | NAT cloud nat0 |

## Endpoints

| Host   | Port | Switch port | VLAN |
| ------ | ---- | ----------- | ---- |
| PC1    | e0   | AS-HQ1 G1/0 | 10   |
| Server | e0   | AS-HQ1 G2/0 | 30   |
| PC2    | e0   | AS-HQ2 G1/0 | 20   |
| PC3    | e0   | AS-BR1 G1/0 | 110  |
| PC4    | e0   | AS-BR2 G1/0 | 120  |
| Ctrl   | ens4 | AS-HQ2 G3/0 | 99   |
