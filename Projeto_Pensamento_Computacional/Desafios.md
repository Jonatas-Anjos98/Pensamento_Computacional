# Desafios Identificados e Soluções Propostas

## 1. Escalabilidade para milhares de usuários simultâneos

**Descrição:**  
Em horários de pico (início de semestre, fim de período de provas), a plataforma pode receber mais de 10 mil acessos simultâneos. O sistema precisa responder com baixa latência e sem queda de serviço.

**Solução proposta:**
- Uso de balanceamento de carga (NGINX, AWS ELB ou HAProxy).
- Cache distribuído (Redis) para sessões, recomendações e consultas frequentes.
- Arquitetura de microsserviços: cada módulo (autenticação, notas, relatórios) escala independentemente.
- Banco de dados com réplicas de leitura e sharding.

## 2. Segurança de dados sensíveis (princípios de Saltzer & Schroeder)

**Descrição:**  
O sistema armazena notas, informações pessoais e senhas. Deve garantir confidencialidade, integridade e disponibilidade, respeitando os princípios clássicos de segurança.

**Solução baseada nos princípios de Saltzer & Schroeder:**
- **Mediação completa:** toda requisição é autenticada e autorizada por um serviço central.
- **Economia de mecanismo:** apenas uma biblioteca de criptografia (bcrypt para senhas, AES para dados em repouso).
- **Mecanismo aberto:** o código de segurança é público e revisável (padrões OWASP).
- **Privilégios mínimos:** cada serviço tem acesso apenas aos dados estritamente necessários.
- **Separação de privilégios:** a geração de relatórios exige aprovação de um coordenador.
- **Facilidade de uso:** segurança não deve travar o usuário comum (ex: login com 2FA opcional).

## 3. Integração com sistemas externos (bibliotecas digitais, APIs)

**Descrição:**  
A plataforma precisa consumir APIs de bibliotecas digitais (ex: Google Books, SciELO, APIs de bibliotecas físicas). Essas APIs podem ser lentas, instáveis ou retornar erros.

**Solução proposta:**
- Padrão **Circuit Breaker** (com Polly ou Resilience4j) para evitar falhas em cascata.
- Cache local dos dados de materiais com TTL (time-to-live) de 1 dia.
- Fila de mensagens (RabbitMQ) para requisições assíncronas (ex: importação de notas de outro sistema).
- Logs centralizados (ELK Stack) para monitorar falhas e tempo de resposta das integrações.

## 4. Disponibilidade e tolerância a falhas

**Descrição:**  
O sistema deve funcionar 24/7, especialmente durante períodos de matrícula e lançamento de notas.

**Solução proposta:**
- Deploy em múltiplas zonas de disponibilidade (cloud).
- Monitoramento proativo (Prometheus + Grafana).
- Plano de disaster recovery com RPO (Recovery Point Objective) de 15 minutos.