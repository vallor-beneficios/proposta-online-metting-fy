# Validação do Entendimento - Reunião Sistema Proposta Online Fase 2

**Data da Reunião:** 24/07/2025  
**Participantes:** Pedro Mandella, Eric Gomes, Thiago Ramos  
**Objetivo:** Validar se o entendimento do fluxo de venda está correto para implementação

---

## Instruções para Pedro

Por favor, revise cada seção abaixo e:
- ✅ **Marque como correto** se o entendimento está adequado
- ❌ **Marque como incorreto** e adicione observações se há algum erro
- ⚠️ **Marque para esclarecer** se precisa de mais detalhes ou esclarecimentos

---

## 1. Fluxo Geral do Sistema

### Entendimento Atual:
O sistema possui 3 portais principais:
1. **Portal do Corretor** - Para vendedores passarem vendas
2. **Portal Back-Office** - Para análise e acompanhamento  
3. **Portal Direto** - Será descontinuado (beneficiário não faz mais própria venda)

**Fluxo completo:**
```
VENDEDOR → Filtros → Seleção Plano → Dados Cliente → Upload Docs → Notifica Cliente
    ↓
CLIENTE → Email Token → Login → Confirma Dados → Declaração Saúde → Finaliza
    ↓  
BACK-OFFICE → Recebe Proposta → Análise Docs → Aprovação/Rejeição

```

**Validação Pedro:**
- [X] ✅ Correto
- [ ] ❌ Incorreto
- [ ] ⚠️ Esclarecer

**Observações/Correções:**
```
o [Espaço para Pedro adicionar comentários]
```

---

## 2. Interface e Experiência do Usuário

### Entendimento Atual:
- **Extremamente intuitiva** - usuários idosos/com dificuldades técnicas
- **Ícones clicáveis** ao invés de formulários complexos
- **Filtros progressivos** - cada seleção elimina opções incompatíveis
- **Navegação lateral** mostrando passos do processo
- **Botões grandes** e visuais claros

### Sequência de Filtros:
1. Tipo de Produto (Coletivo/Empresarial)
2. Estado/Cidade  
3. Profissão → Entidade (automático)
4. Abrangência (Nacional/Estadual/Grupo Municípios)
5. Coparticipação (Com/Sem)
6. Cobertura (Ambulatorial, Ambulatorial Hospitalar com Obstetrícia, Ambulatorial Hospitalar sem Obstetrícia e Odontológico)
7. Acomodação (Enfermaria/Apartamento)
8. Idade dos beneficiários (Titular e Dependentes)

**Validação Pedro:**
- [X] ✅ Correto
- [ ] ❌ Incorreto  
- [ ] ⚠️ Esclarecer

**Observações/Correções:**
```
[Espaço para Pedro adicionar comentários]
```

---

## 3. Cadastros Necessários (Faltantes no Sistema Atual)

### Entendimento Atual:

#### 3.1 Cadastro de Profissões
- **Estrutura:** ID, Nome da Profissão, Status
- **Relacionamento:** N:N com Entidades
- **Exemplos:** Advogado→OAB, Estudante→Abraeste/Abraune, Comerciário→Entidade específica

#### 3.2 Formas de Pagamento  
- **Boleto Bancário** (padrão)
- **Consignado em Folha** (apenas Governo Pernambuco)

#### 3.3 Ajuste no Cadastro de Entidades
- Vinculação com Profissões

**Validação Pedro:**
- [ ] ✅ Correto
- [ ] ❌ Incorreto
- [X] ⚠️ Esclarecer

**Observações/Correções:**
```
No momento da venda precisamos que seja informado a forma de pagamento escolhida pelo cliente. EX: Consignado em folha(descontado diretamente na folha de pagamento do Servidor Público do Estado de Pernambuco) e Boleto Bancário.
Precisamos que dentro do cadastro de planos e produtos seja acrescido duas caixas de seleção: 
Caixa 1: Boleto Bancário 
Caixa 2: Consignado em Folha 

No final da venda, onde consta um checklist para o corretor com as informações sobre o plano que foi vendido, deve informar qual a forma de pagamento daquele plano.

```
---

## 4. Regras de Negócio Críticas

### 4.1 Declaração de Saúde - Segregação OBRIGATÓRIA
**Entendimento:** 
- Vendedor **NÃO pode ver** declaração de saúde
- Apenas Cliente e Back-office têm acesso
- Objetivo: evitar influência nas respostas do beneficiário

### 4.2 CPT (Cobertura Parcial Temporária)
**Entendimento:**
- Acionada quando cliente responde "SIM" em questões de saúde
- Máximo 24 meses de restrição
- Cliente pode aderir ao plano mas não tratar condição pré-existente

### 4.3 Cálculo de Valores
**Entendimento:**
- Valores calculados automaticamente por faixa etária
- Mostrar **todas as faixas** no documento (transparência)
- Somar titular + dependentes = valor total

### 4.4 Vigências
**Entendimento:**
- Sempre 3 opções disponíveis (atual + 2 próximas)
- Rotação automática quando uma fecha

**Validação Pedro:**
- [X] ✅ Correto
- [ ] ❌ Incorreto
- [ ] ⚠️ Esclarecer

**Observações/Correções:**
```
[Espaço para Pedro adicionar comentários]
```

---

## 5. Integrações e APIs Necessárias

### Entendimento Atual:

#### 5.1 Consulta CPF  
- Possibilidade de puxar nome completo
- Validação do documento

#### 5.2 Sistema de Email
**Templates necessários:**
- Notificação para Cliente (com token de acesso)
- Notificação de Pendência para Vendedor

#### 5.3 Geração de PDF Dinâmica
- Campos preenchidos aparecem em **azul**
- Texto fixo em **preto**
- Marca d'água "RASCUNHO" no preview
- Assinatura eletrônica

**Validação Pedro:**
- [X] ✅ Correto
- [ ] ❌ Incorreto
- [ ] ⚠️ Esclarecer

**Observações/Correções:**
```
[Espaço para Pedro adicionar comentários]
```

---

## 6. Estrutura do Documento/Contrato

### Entendimento da Composição:
1. **Proposta de Adesão** (dados dinâmicos)
2. **Contrato** (fixo, apenas assinatura)  
3. **Aditivo de Carência** (por operadora, fixo)
4. **Aditivo de Produto** (tabela de preços **DINÂMICA**)
5. **LGPD** (fixo)
6. **Manual de Orientação** (fixo) 
7. **Ficha de Associação** (dados dinâmicos)
8. **Aditivos Especiais** (quando aplicável - ex: desconto aniversário)

### PONTO CRÍTICO - Tabela de Preços:
**Problema atual:** PDFs estáticos (demora 7 dias para atualizar)  
**Solução:** Valores dinâmicos do sistema em tempo real

**Validação Pedro:**
- [X] ✅ Correto
- [ ] ❌ Incorreto
- [ ] ⚠️ Esclarecer

**Observações/Correções:**
```
[Espaço para Pedro adicionar comentários]
```

---

## 7. Processo do Cliente (Token de Acesso)

### Entendimento do Fluxo:
1. Cliente recebe email com **token único**
2. Acessa sistema com **CPF** (usuário) + **Token** (senha)
3. Confirma dados preenchidos pelo vendedor
4. Lê carta de orientação
5. Preenche **declaração de saúde** (exclusivo)
6. Finaliza proposta

### Validação de Dados no Email:
- Nome do Cliente
- Nome do Vendedor/Corretor  
- Link de acesso
- Token de segurança

**Validação Pedro:**
- [X] ✅ Correto
- [ ] ❌ Incorreto
- [ ] ⚠️ Esclarecer

**Observações/Correções:**
```
[Espaço para Pedro adicionar comentários]
```

---

## 8. Pós-Venda e Gestão de Pendências

### Entendimento do Processo:
1. Proposta vai para back-office automaticamente
2. Back-office analisa documentação
3. Se há pendência → notifica vendedor por **email**
4. Vendedor acessa sistema e vê pendência
5. Vendedor pode **anexar novos documentos** para sanar
6. Status são atualizados em tempo real

### Estados da Proposta:
- Iniciada → Notificada → Em Preenchimento → Finalizada → Em Análise → Com Pendência → Aprovada/Cancelada

**Validação Pedro:**
- [X] ✅ Correto
- [ ] ❌ Incorreto
- [ ] ⚠️ Esclarecer

**Observações/Correções:**
```
[Espaço para Pedro adicionar comentários]
```

---

## 9. Campos Obrigatórios e Opcionais

### Campos Obrigatórios Identificados (marcados com *):
- CPF
- Email (diferente do login do vendedor)
- Data de nascimento  
- Nome da mãe
- Celular
- Estado civil
- Cadastro Nacional de Saúde (CNS)

### Campos Opcionais:
- Telefone residencial
- Número de Declaração de Nascido Vivo
- Órgão emissor

**Validação Pedro:**
- [X] ✅ Correto
- [ ] ❌ Incorreto
- [ ] ⚠️ Esclarecer

**Observações/Correções:**
```
[Espaço para Pedro adicionar comentários]
```

---

## 10. Upload de Documentos

### Entendimento do Sistema:
- **Flexível:** aceita PDF único com todos os documentos OU arquivos separados
- **Tipos de documento:**
  - Documento de identificação
  - Ficha associativa  
  - Comprovante de residência
  - Documento para redução de carência
  - Comprovante de vínculo na entidade
  - Cartão Nacional de Saúde
  - Documentação de vínculo estudantil
  - Comprovante de vínculo com empresa

**Validação Pedro:**
- [X] ✅ Correto
- [ ] ❌ Incorreto
- [ ] ⚠️ Esclarecer

**Observações/Correções:**
```
[Espaço para Pedro adicionar comentários]
```

---

## 11. Pontos que Precisam de Esclarecimento

### Questões Identificadas Durante a Reunião:

1. **Lista completa de Profissões e Entidades** - Pedro vai fornecer
2. **Templates de documentos específicos** - Pedro vai fornecer  
3. **Manual passo a passo com prints** - Pedro vai criar
4. **Forma de pagamento deve aparecer na proposta?** - Pedro confirmou que SIM

**Validação Pedro:**
- [ ] ✅ Correto - vou fornecer estas informações
- [ ] ❌ Incorreto - há outros pontos pendentes
- [X] ⚠️ Esclarecer - preciso ajustar algo

**Observações/Correções:**
```
PROFISSÕES E ENTIDADES:

ADMINISTRADOR = CRA - BAHIA
ADVOGADO = OAB GUARATINGUETÁ / OAB LORENA / OAB CACHOEIRA PAULISTA / OAB CRUZEIRO / OAB IPATINGA 
APOSENTADO, PENSIONISTA E IDOSOS = SNAPFS / SINDNAPI
ASSISTENTE SOCIAL = SASB
AUTÔNOMO = ABRAVA
COMERCIÁRIO = ANASERV / SEC
CORRETOR DE SEGUROS = SINCOR 
EMPRESÁRIO = ANASERV
ESTUDANTE = AEB / ABRAEST / ABRAUNI / FESN
FEIRANTES = SINDIFEIRANTES 
PROFISSIONAL LIBERAL = ANASERV
REPRESENTANTE COMERCIAL = CORE
SERVIDOR PÚBLICO = AASP
TAXISTA = FECOMBASE
TRABALHADOR NO RAMO AGRÍCOLA = SINTAGRO
TRABALHADOR NO RAMO DE SERVIÇOS = FECOMBASE
SERVIDOR PÚBLICO DO ESTADO DO RIO DE JANEIRO = INSERV RJ
POLICIAIS E BOMBEIROS MILITARES = ASPRA
SERVIDORES DA FUNDAÇÃO UNIVERSIDADE FEDERAL DO VALE DO SÃO FRANCISCO = ASSUNIVASF
SERVIDORES PÚBLICOS MUNICIPAIS DE JUAZEIRO = SINSERP
ASSOCIACAO BENEFICIENTE EDUCACIONAL E RECREATIVO DOS PRACAS DA POLÍCIA MILITAR E DO CORPO DE BOMBEIROS MILITAR DO ESTADO DA BAHIA = APPMBM
UNIÃO NACIONAL DOS PROFISSIONAIS LIBERAIS = UNIPROLI
ASSOCIACAO BRASILEIRA DOS VENDEDORES AUTONOMOS E AMBULANTES = ANAVA
SINDICATOS TRABALHADORES INDUSTRIAIS METALURGICOS MECANICOS E MATERIAIS ELETRICOS DE ITAJUBA = CSP
ASSOCIAÇÃO DOS PROFISSIONAIS DE BELEZA DO VALE DO SÃO FRANCISCO = ASSOCIAÇÃO DOS PROFISSIONAIS DE BELEZA DO VALE DO SÃO FRANCISCO



<img width="661" height="521" alt="image" src="https://github.com/user-attachments/assets/98984157-4f3a-4fbf-9203-431c8befcea3" />


```

---

## 12. Próximos Passos Confirmados

### Ações da Equipe de Desenvolvimento:
1. Mastigar e documentar tecnicamente os requisitos
2. Criar estrutura dos novos cadastros necessários
3. Implementar filtros progressivos na interface
4. Desenvolver sistema de tokens e notificações

### Ações do Pedro:
1. Fornecer manual detalhado com prints passo a passo
2. Listar profissões e entidades completas
3. Fornecer templates de comunicação
4. Validar casos de uso de modelos de contrato

**Validação Pedro:**
- [X] ✅ Correto - concordo com as ações
- [ ] ❌ Incorreto - preciso ajustar algo
- [ ] ⚠️ Esclarecer - tenho dúvidas sobre algum ponto

**Observações/Correções:**
```
[Espaço para Pedro adicionar comentários]
```

---

## Resumo da Validação

**Pedro, por favor preencha:**

### Pontos que estão CORRETOS no entendimento:
```
TODOS OS FLUXOS QUE EU MARQUEI CORRETO, ESTÃO DEVIDAMENTE VALIDADOS E AS INFORMAÇÕES FORAM DEVIDAMENTE ENTENDIDAS. NÃO TENHO DEMAIS OBSERVAÇÕES. 
```

### Pontos que precisam de CORREÇÃO:
```
NÃO HÁ CORREÇÕES A SEREM REALIZADAS. 
```

### Pontos que precisam de mais ESCLARECIMENTO:
```
## 3. Cadastros Necessários (Faltantes no Sistema Atual)
No momento da venda precisamos que seja informado a forma de pagamento escolhida pelo cliente. EX: Consignado em folha(descontado diretamente na folha de pagamento do Servidor Público do Estado de Pernambuco) e Boleto Bancário.
Precisamos que dentro do cadastro de planos e produtos seja acrescido duas caixas de seleção: 
Caixa 1: Boleto Bancário 
Caixa 2: Consignado em Folha 

No final da venda, onde consta um checklist para o corretor com as informações sobre o plano que foi vendido, deve informar qual a forma de pagamento daquele plano.

```

### Informações ADICIONAIS que não foram mencionadas:
```
Não se aplica. 
```

---

**Data de Validação:** 25/07/2025
**Assinatura/Confirmação Pedro:** Pedro H. Mandella

---

## Observações Finais

Este documento serve como checkpoint para garantir que a implementação seja feita conforme suas necessidades reais. Qualquer dúvida ou correção, por favor documente claramente para evitarmos retrabalho.

**Contato para dúvidas:** Eric Gomes / Thiago Ramos
