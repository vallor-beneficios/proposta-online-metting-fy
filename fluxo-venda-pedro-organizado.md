# Fluxo de Venda - Sistema de Proposta Online Fase 2

## Visão Geral

Este documento organiza e estrutura o fluxo de venda apresentado por Pedro Mandella, detalhando o processo completo desde o acesso do corretor até a finalização da venda e envio para o back-office.

## Participantes da Reunião
- Pedro Mandella (Apresentador)
- Eric Gomes
- Thiago Ramos

## Contexto

O fluxo apresentado detalha o funcionamento do sistema atual da Plânio e serve como base para a implementação da Fase 2 do novo sistema. A prioridade é manter a simplicidade e intuitividade do processo, especialmente considerando que muitos vendedores têm dificuldades com tecnologia.

---

## 1. Estrutura Inicial do Sistema

### 1.1 Tela Inicial
A tela inicial possui três opções principais:
- **Portal Direto** (será descontinuado) - onde o beneficiário fazia sua própria venda
- **Portal do Corretor** - exclusivo para vendedores passarem vendas
- **Portal Back-Office** - para análise e acompanhamento de vendas

> **Importante:** O Portal Direto não será implementado no novo sistema, pois não se trabalha mais com beneficiários fazendo suas próprias vendas.

### Imagens de Referência:
![Menu inicial do sistema](capturas-telas/Screenshot%202025-07-24%20at%2009.44.25.png)

---

## 2. Fluxo do Vendedor/Corretor

### 2.1 Login
- O vendedor acessa o Portal do Corretor
- Realiza login com suas credenciais
- **Nota:** Vendedor e corretor são sinônimos no sistema

### 2.2 Processo de Venda - Interface Intuitiva

#### Princípio de Design Fundamental
> "Eu preciso que a passagem da venda seja uma coisa muito intuitiva... são pessoas mais idosas, são pessoas mais velhas, muitas vezes analfabetos de informática" - Pedro Mandella

O sistema deve:
- Trabalhar com **ícones clicáveis**
- Evitar formulários de preenchimento complexos
- Usar interface visual com desenhos ilustrativos
- Cada seleção funciona como um filtro, eliminando opções incompatíveis

### Imagens de Referência:
![Tela de boas-vindas](capturas-telas/Screenshot%202025-07-24%20at%2009.47.27.png)

![Seleção por ícones](capturas-telas/Screenshot%202025-07-24%20at%2009.47.37.png)

---

## 3. Etapas da Venda (Filtros Sequenciais)

### 3.1 Tipo de Produto
**Opções:**
- Coletivo por Adesão (através de entidades/sindicatos)
- Empresarial (PME)

> **Filtro aplicado:** Ao selecionar Coletivo por Adesão, produtos empresariais são eliminados

### Imagens de Referência:
![Seleção do tipo de produto](capturas-telas/Screenshot%202025-07-24%20at%2009.47.58.png)

### 3.2 Localização
**Seleção de:**
- Estado
- Cidade

> **Filtro aplicado:** Apenas produtos disponíveis na região selecionada serão exibidos

### Imagens de Referência:
![Seleção de estado](capturas-telas/Screenshot%202025-07-24%20at%2009.48.19.png)

![Seleção de cidade](capturas-telas/Screenshot%202025-07-24%20at%2009.48.32.png)

### 3.3 Profissão e Entidade
**Processo:**
1. Seleciona-se a profissão do beneficiário
2. Sistema automaticamente puxa as entidades/sindicatos associados
3. Exemplo: Advogado → OAB, Estudante → Abraeste/Abraune

> **Ponto de Atenção:** Necessário criar cadastro de profissões no sistema

### Imagens de Referência:
![Seleção de profissão](capturas-telas/Screenshot%202025-07-24%20at%2009.48.40.png)

### 3.4 Abrangência do Plano
**Opções:**
- Nacional (atendimento em todo Brasil)
- Estadual (apenas no estado selecionado)
- Grupo de Municípios (cidades específicas dentro do estado)

### Imagens de Referência:
![Seleção de abrangência](capturas-telas/Screenshot%202025-07-24%20at%2009.49.36.png)

### 3.5 Características do Plano
**Seleções incluem:**
- Coparticipação (com ou sem)
- Tipo de cobertura:
  - Ambulatorial
  - Ambulatorial + Hospitalar com Obstetrícia
  - Ambulatorial + Hospitalar sem Obstetrícia
  - Odontológico
- Acomodação (Enfermaria ou Apartamento)

### Imagens de Referência:
![Seleção de coparticipação](capturas-telas/Screenshot%202025-07-24%20at%2009.50.03.png)

### 3.6 Dados dos Beneficiários
**Informações necessárias:**
- Idade do titular
- Quantidade e idade dos dependentes (se houver)

> **Funcionalidade:** Sistema permite adicionar múltiplos beneficiários através do botão "+"

### Imagens de Referência:
![Informação de idade](capturas-telas/Screenshot%202025-07-24%20at%2009.51.12.png)

---

## 4. Seleção do Plano

### 4.1 Exibição de Planos Disponíveis
Após aplicar todos os filtros, o sistema exibe:
- Operadoras disponíveis
- Planos com suas características
- **Valores já calculados para a faixa etária informada**
- Código ANS de cada plano

### Imagens de Referência:
![Lista de planos disponíveis](capturas-telas/Screenshot%202025-07-24%20at%2009.51.19.png)

![Detalhes dos planos](capturas-telas/Screenshot%202025-07-24%20at%2009.51.25.png)

### 4.2 Informações Exibidas por Plano
- Nome do plano
- Operadora
- Segmentação
- Tipo de acomodação
- Abrangência
- Coparticipação
- Valor mensal
- Código ANS

---

## 5. Preenchimento de Dados do Cliente

### 5.1 Dados Pessoais
**Campos obrigatórios (marcados com *):**
- CPF (sistema pode puxar nome automaticamente)
- Email (diferente do email de login do vendedor)
- Data de nascimento
- Nome da mãe
- Celular
- Estado civil
- Cadastro Nacional de Saúde (CNS)

**Campos opcionais:**
- Telefone residencial
- Número de Declaração de Nascido Vivo
- Órgão emissor

### Imagens de Referência:
![Formulário de dados pessoais](capturas-telas/Screenshot%202025-07-24%20at%2009.51.33.png)

![Continuação do formulário](capturas-telas/Screenshot%202025-07-24%20at%2009.51.39.png)

### 5.2 Endereço
- CEP (puxa endereço automaticamente)
- Logradouro
- Número
- Complemento
- Bairro
- Cidade
- Estado

### Imagens de Referência:
![Dados de endereço](capturas-telas/Screenshot%202025-07-24%20at%2009.51.46.png)

### 5.3 Documentação
**Opções de anexo:**
- Documento de identificação
- Ficha associativa
- Comprovante de residência
- Documento para análise de redução de carência
- Comprovante de vínculo na entidade
- Cartão Nacional de Saúde
- Documentação comprobatória do vínculo estudantil
- Comprovante de vínculo com a empresa

> **Facilidade:** Sistema aceita PDF único com todos os documentos ou anexos separados

### Imagens de Referência:
![Upload de documentos](capturas-telas/Screenshot%202025-07-24%20at%2009.52.08.png)

### 5.4 Seleção de Vigência
- Sistema sempre disponibiliza 3 vigências: atual e duas próximas
- Quando uma vigência fecha, é automaticamente substituída pela seguinte

### Imagens de Referência:
![Seleção de vigência](capturas-telas/Screenshot%202025-07-24%20at%2009.53.49.png)

### 5.5 Forma de Pagamento
- **Padrão:** Boleto bancário
- **Exceção:** Governo de Pernambuco - consignado em folha

> **Melhoria sugerida:** Incluir forma de pagamento na proposta para evitar confusões

---

## 6. Resumo e Visualização da Proposta

### 6.1 Resumo da Contratação
Sistema exibe todas as informações para conferência:
- Data da proposta
- CPF do contratante
- Tipo de contratação
- Operadora e plano
- Registro ANS
- Características do plano
- Quantidade de beneficiários
- Valor total
- Entidade
- Vigência

### Imagens de Referência:
![Resumo da contratação](capturas-telas/Screenshot%202025-07-24%20at%2009.54.37.png)

### 6.2 Visualização do Rascunho (Preview)
**Estrutura do documento gerado:**

1. **Proposta de Adesão**
   - Dados preenchidos aparecem em azul
   - Texto fixo em preto
   - Assinatura eletrônica e data

2. **Contrato (páginas fixas)**
   - Resumo das características gerais
   - Elegibilidade
   - Direitos de contratação
   - Procedimentos de cancelamento
   - Cobertura e prazos
   - Apenas assinatura e data são preenchidas

3. **Aditivo de Carência**
   - Específico por operadora (não por plano)
   - Conteúdo fixo
   - Apenas assinatura e data

4. **Aditivo de Produto (Tabela de Preços)**
   - **PONTO CRÍTICO:** No novo sistema, valores devem vir dinamicamente do cadastro
   - Exibe todas as faixas etárias (para transparência com cliente)
   - Tabela de coparticipação (quando aplicável)
   - Municípios atendidos (para planos de grupo de municípios)

5. **LGPD**
   - Informativo sobre proteção de dados
   - Lei nº 13.709/2018
   - Apenas assinatura e data

6. **Ficha de Associação**
   - Específica da entidade/sindicato
   - Preenchida com dados do beneficiário
   - Confirma filiação à entidade

7. **Aditivos Especiais** (quando aplicável)
   - Exemplo: Desconto de aniversário da empresa
   - Termos e condições especiais
   - Período de vigência da condição

### Imagens de Referência:
![Páginas do documento - Início](capturas-telas/Screenshot%202025-07-24%20at%2009.57.29.png)

![Páginas do documento - Final](capturas-telas/Screenshot%202025-07-24%20at%2010.17.07.png)

---

## 7. Notificação e Finalização pelo Cliente

### 7.1 Notificação por Email
**Conteúdo do email:**
- Saudação personalizada
- Informação sobre o corretor que iniciou a proposta
- Link para acesso
- Token de acesso único

### Imagens de Referência:
![Email de notificação](capturas-telas/Screenshot%202025-07-24%20at%2010.17.26.png)

![Conteúdo do email](capturas-telas/Screenshot%202025-07-24%20at%2010.17.32.png)

### 7.2 Acesso do Cliente
1. Cliente clica no link recebido
2. Informa CPF como usuário
3. Cola o token como senha
4. Acessa o sistema

### Imagens de Referência:
![Tela de login do cliente](capturas-telas/Screenshot%202025-07-24%20at%2010.18.18.png)

### 7.3 Processo de Finalização

#### Confirmação de Dados
- Cliente visualiza e confirma informações da proposta
- Verifica plano, valor e dados pessoais

### Imagens de Referência:
![Confirmação de dados](capturas-telas/Screenshot%202025-07-24%20at%2010.18.27.png)

#### Carta de Orientação
- Template fixo com orientações ao beneficiário
- Cliente deve ler e concordar

### Imagens de Referência:
![Carta de orientação](capturas-telas/Screenshot%202025-07-24%20at%2010.18.49.png)

#### Declaração de Saúde
**Ponto Crítico:**
- **NÃO é exibida para o vendedor** (para evitar influência nas respostas)
- Cliente preenche diretamente
- Campos incluem:
  - Peso e altura
  - Perguntas sobre condições de saúde
  - Justificativas quando responde "Sim"

**CPT (Cobertura Parcial Temporária):**
- Aplicada quando cliente declara condições pré-existentes
- Vigência máxima: 24 meses
- Durante este período, não pode tratar a condição específica
- Proteção financeira para a operadora

### Imagens de Referência:
![Declaração de saúde - Início](capturas-telas/Screenshot%202025-07-24%20at%2010.19.06.png)

![Declaração de saúde - Final](capturas-telas/Screenshot%202025-07-24%20at%2010.19.55.png)

#### Finalização
- Cliente confirma forma de pagamento
- Visualiza resumo final
- Pode ver preview do documento completo
- Finaliza a proposta

### Imagens de Referência:
![Confirmação final](capturas-telas/Screenshot%202025-07-24%20at%2010.26.31.png)

![Proposta recebida com sucesso](capturas-telas/Screenshot%202025-07-24%20at%2010.26.42.png)

---

## 8. Pós-Venda e Back-Office

### 8.1 Fluxo após Finalização
1. Proposta é enviada automaticamente para o back-office
2. Back-office inicia análise documental
3. Vendedor pode acompanhar status da venda no sistema

### 8.2 Papel do Vendedor no Pós-Venda
**Funcionalidades disponíveis:**
- Visualizar status das vendas
- Identificar em qual setor está a proposta
- Verificar se foi aprovada, em análise ou cancelada
- Sanar pendências documentais

### 8.3 Sistema de Pendências
**Processo:**
1. Back-office identifica pendência (ex: documento inválido)
2. Sistema notifica vendedor via email
3. Vendedor acessa sistema e visualiza pendência
4. Anexa novo documento para sanar pendência

> **Comunicação:** Notificações devem ser enviadas preferencialmente por email

---

## 9. Requisitos Técnicos Identificados

### 9.1 Cadastros Necessários
1. **Profissões**
   - Cadastro independente
   - Vinculação com entidades (N:N)

2. **Formas de Pagamento**
   - Boleto bancário
   - Consignado em folha

3. **Modelos de Contrato**
   - Blocos dinâmicos com dados do sistema
   - Integração com tabelas de preço

### 9.2 Integrações
- **CEP:** Busca automática de endereço
- **CPF:** Possibilidade de buscar dados básicos
- **Email:** Sistema de notificações
- **Geração de PDF:** Com preenchimento dinâmico

### 9.3 Melhorias Sugeridas
1. **Tabela de Preços Dinâmica**
   - Eliminar necessidade de atualizar PDFs
   - Valores em tempo real do sistema

2. **Forma de Pagamento na Proposta**
   - Evitar confusão sobre boleto vs consignado

3. **Interface Responsiva**
   - Manter simplicidade visual
   - Priorizar usabilidade para usuários não técnicos

---

## 10. Observações Finais

### Princípios de Design
- **Simplicidade é fundamental** - muitos usuários têm dificuldades com tecnologia
- **Visual sobre textual** - usar ícones e imagens sempre que possível
- **Filtros progressivos** - cada seleção elimina opções incompatíveis
- **Transparência de valores** - mostrar todas as faixas etárias para o cliente

### Próximos Passos
1. Documentação detalhada com prints passo a passo (a ser fornecida por Pedro)
2. Definição de templates de comunicação
3. Estruturação dos casos de uso de modelos de contrato
4. Implementação dos cadastros auxiliares

---

## Anexo: Lista de Capturas de Tela

Todas as capturas de tela mencionadas neste documento estão disponíveis no diretório `capturas-telas/` do projeto.

Total de imagens capturadas: 36 screenshots documentando todo o fluxo apresentado.