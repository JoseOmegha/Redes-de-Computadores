# UNIBRAS - Projeto de Redes de Computadores
## Configuração e Análise dos Protocolos de Roteamento Dinâmico IPv6
### RIPng, EIGRPv6 e OSPFv3

> Trabalho Prático — Disciplina de Redes de Computadores

---

## 👥 Informações do Projeto

### 📚 Disciplina
**Redes de Computadores**

### 👨‍🎓 Aluno
- José Antônio dos Santos Filho

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
```plaintext
ipv6 unicast-routing
interface f0/0
 ipv6 address 2001:DB8:CAFE:1::1/64
 ipv6 rip RIPNG enable
interface s0/3/0
 ipv6 address 2001:DB8:CAFE:F::1/127
 ipv6 rip RIPNG enable
ipv6 router rip RIPNG
