# Relatório Técnico — Protocolos de Roteamento Dinâmico IPv6
## EIGRPv6, OSPFv3 e RIPng

### 📚 Disciplina
Redes de Computadores

### 👨‍🎓 Aluno
José Antônio dos Santos Filho

### 👨‍🏫 Orientador
Prof. Francismar Alves Martins Junior

---

## 📝 Resumo
Este trabalho prático implementa e compara três protocolos de roteamento dinâmico em IPv6: **EIGRPv6**, **OSPFv3** e **RIPng**, em uma topologia composta por três roteadores interligados em série. Cada roteador possui uma interface loopback representando uma rede local e enlaces seriais ponto-a-ponto. O objetivo é configurar, verificar e analisar o funcionamento de cada protocolo, validando a conectividade entre todas as redes.

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

### EIGRPv6
- **Tipo:** Híbrido (DUAL)  
- **AS Number:** 10  
- **Configuração:** habilitado por interface com `ipv6 eigrp 10`  
- **Verificação:**  
  - `show ipv6 eigrp neighbors`  
  - `show ipv6 route eigrp`  

---

### OSPFv3
- **Tipo:** Estado de enlace  
- **Área:** 0 (backbone)  
- **Configuração:** habilitado por interface com `ipv6 ospf 1 area 0`  
- **Verificação:**  
  - `show ipv6 ospf neighbor`  
  - `show ipv6 route ospf`  

---

### RIPng
- **Tipo:** Vetor de distância  
- **Métrica:** Número de saltos  
- **Configuração:** habilitado por interface com `ipv6 rip RIPNG enable`  
- **Verificação:**  
  - `show ipv6 rip`  
  - `show ipv6 route rip`  

---

## 📊 Resultados e Análise

- **EIGRPv6:** Convergência rápida, vizinhanças formadas corretamente, rotas aprendidas com sucesso.  
- **OSPFv3:** Escalabilidade alta, vizinhanças estáveis, rotas aprendidas e banco de dados LSA completo.  
- **RIPng:** Funcionou corretamente, mas apresenta convergência lenta e limitação de saltos.  
- **Testes de conectividade:** Todos os roteadores conseguiram ping e traceroute entre as loopbacks.  

---

## 🎓 Conclusões

1. **EIGRPv6** oferece bom desempenho e convergência rápida, ideal para redes médias.  
2. **OSPFv3** é o protocolo mais robusto e escalável, padrão em ambientes corporativos.  
3. **RIPng** é útil para aprendizado inicial, mas limitado para redes grandes.  
4. Todos os protocolos garantiram comunicação plena entre as redes IPv6 configuradas.  

---

## ✅ Checklist de Entrega

- [x] Topologia com 3 roteadores  
- [x] Interfaces loopback configuradas  
- [x] Roteamento IPv6 habilitado  
- [x] EIGRPv6 configurado e testado  
- [x] OSPFv3 configurado e testado  
- [x] RIPng configurado e testado  
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
