# UNIBRAS - Projeto de Redes de Computadores
## Configuração e Análise dos Protocolos de Roteamento Dinâmico IPv6
### RIPng, EIGRPv6 e OSPFv3

> Trabalho Prático — Disciplina de Redes de Computadores

---

## 👥 Informações do Projeto

### 📚 Disciplina
**Redes de Computadores**

### 👨‍🎓 Aluno
- José [Seu Sobrenome]

### 👨‍🏫 Orientador
- Prof. Francismar Alves Martins Junior

---

## 🎯 Objetivo da Atividade

Configurar e analisar o funcionamento dos principais protocolos de roteamento dinâmico em redes IPv6 (RIPng, EIGRPv6 e OSPFv3), através de uma topologia composta por três roteadores interligados em série, utilizando simuladores de rede.

---

## 📋 Requisitos Obrigatórios

1. **Topologia:** 3 roteadores interligados em série (R1–R2–R3)  
2. **Interfaces por Roteador:**  
   - 1 interface Loopback (rede local)  
   - 2 interfaces de enlace IPv6 (comunicação entre roteadores)  
3. **Endereçamento:** IPv6 com prefixo `2001:DB8::/32`  
4. **Roteamento:** `ipv6 unicast-routing` habilitado em todos os roteadores  
5. **Protocolos:** Implementação completa de RIPng, EIGRPv6 e OSPFv3  

---

## 📊 Critérios de Avaliação

| Item | Pontuação | Descrição |
|------|-----------|-----------|
| RIPng Configurado | 0,5 pt | Funcionamento correto |
| EIGRPv6 Configurado | 0,5 pt | Funcionamento correto |
| OSPFv3 Configurado | 0,5 pt | Funcionamento correto |
| Organização e Documentação | 0,3 pt | Estrutura no GitHub |
| Demonstração em Vídeo | 0,2 pt | Clareza e completude |
| Bônus: Falha e Reconvergência | 0,2 pt | Teste opcional |
| **TOTAL** | **1,5 pt** | até 1,7 pt com bônus |

---

## 🔬 Relatório Técnico

### 📝 Resumo
Este trabalho implementa e compara três protocolos de roteamento dinâmico em IPv6: **RIPng**, **EIGRPv6** e **OSPFv3**, em uma topologia composta por três roteadores interligados em série. Cada roteador possui uma interface loopback representando uma rede local e enlaces seriais ponto-a-ponto. O objetivo é configurar, verificar e analisar o funcionamento de cada protocolo, validando a conectividade entre todas as redes.

---

## ⚡️ Metodologia

### 🔧 Ambiente Utilizado
- **Simulador:** Cisco Packet Tracer  
- **Equipamentos:** 3 Roteadores Cisco série 2901  
- **Protocolo de Rede:** IPv6  
- **Endereçamento Base:** `2001:DB8::/32`  
- **Links:** Seriais ponto-a-ponto (/127)  
- **Redes Locais:** Loopbacks (/64)  

### 📍 Endereçamento IPv6
| Roteador | Loopback | Link para R2 | Link para R3 |
|----------|----------|--------------|--------------|
| **R1** | 2001:DB8:CAFE:1::1/64 | 2001:DB8:CAFE:F::1/127 | N/A |
| **R2** | 2001:DB8:CAFE:2::1/64 | 2001:DB8:CAFE:F::0/127 | 2001:DB8:CAFE:E::0/127 |
| **R3** | 2001:DB8:CAFE:4::1/64 | N/A | 2001:DB8:CAFE:E::1/127 |

---

## 🔹 Configuração dos Protocolos

### RIPng
ipv6 unicast-routing
interface f0/0
 ipv6 address 2001:DB8:CAFE:1::1/64
 ipv6 rip RIPNG enable
interface s0/3/0
 ipv6 address 2001:DB8:CAFE:F::1/127
 ipv6 rip RIPNG enable
ipv6 router rip RIPNG

---

### EIGRPv6
ipv6 unicast-routing
ipv6 router eigrp 10
 router-id 1.1.1.1
 no shutdown
interface f0/0
 ipv6 address 2001:DB8:CAFE:1::1/64
 ipv6 eigrp 10
interface s0/3/0
 ipv6 address 2001:DB8:CAFE:F::1/127
 ipv6 eigrp 10

---

### OSPFv3
ipv6 unicast-routing
ipv6 router ospf 1
 router-id 1.1.1.1
interface f0/0
 ipv6 address 2001:DB8:CAFE:1::1/64
 ipv6 ospf 1 area 0
interface s0/3/0
 ipv6 address 2001:DB8:CAFE:F::1/127
 ipv6 ospf 1 area 0

---

## 📂 Estrutura do Repositório
```
roteamento-ipv6/
├── README.md
├── assets/
│   └── unibras-logo.png
├── configs/
│   ├── RIPng/
│   │   ├── R1-ripng.txt
│   │   ├── R2-ripng.txt
│   │   └── R3-ripng.txt
│   ├── EIGRPv6/
│   │   ├── R1-eigrpv6.txt
│   │   ├── R2-eigrpv6.txt
│   │   └── R3-eigrpv6.txt
│   └── OSPFv3/
│       ├── R1-ospfv3.txt
│       ├── R2-ospfv3.txt
│       └── R3-ospfv3.txt
├── topologias/
│   ├── ripng.pkt
│   ├── eigrpv6.pkt
│   └── ospfv3.pkt
├── prints/
│   ├── RIPng/
│   ├── EIGRPv6/
│   └── OSPFv3/
└── docs/
    └── relatorio.md
```
---

## ✅ Checklist de Entrega
- [x] Topologia com 3 roteadores
- [x] Interfaces loopback configuradas
- [x] Roteamento IPv6 habilitado
- [x] RIPng configurado e testado
- [x] EIGRPv6 configurado e testado
- [x] OSPFv3 configurado e testado
- [x] Conectividade validada (ping/traceroute)
- [x] Repositório GitHub organizado
- [x] Vídeo demonstrativo no YouTube

---

## 📅 Histórico de Versões

| Versão | Data | Descrição |
|--------|------|-----------|
| v1.0.0 | 30/11/2025 | Conclusão do projeto com documentação completa |
| v0.9.0 | 29/11/2025 | Implementação final do OSPFv3 e testes |
| v0.7.0 | 28/11/2025 | Implementação do EIGRPv6 |
| v0.5.0 | 27/11/2025 | Implementação do RIPng |
| v0.1.0 | 26/11/2025 | Criação da topologia base |

---

## 📋 Informações Importantes

- **Instituição:** UNIBRAS  
- **Aluno:** José Antônio dos Santos Filho 
- **Orientador:** Prof. Francismar Alves Martins Junior  
- **Simulador:** Cisco Packet Tracer  
- **Data de Conclusão:** 30 de novembro de 2025  

**Aviso Legal:**  
- Cisco Packet Tracer é de propriedade da Cisco Systems, Inc.  
- Este projeto é para fins educacionais.  
