# Requisitos Técnicos e Integrações - Sistema de Proposta Online

## 1. Novos Cadastros Necessários

### 1.1 Cadastro de Profissões
**Estrutura básica:**
```
- ID
- Nome da Profissão
- Status (Ativo/Inativo)
```

**Relacionamentos:**
- N:N com Entidades (uma profissão pode ter várias entidades, uma entidade pode atender várias profissões)

**Exemplos mencionados:**
- Advogado → OAB
- Estudante → Abraeste, Abraune, FESN
- Comerciário → (entidade específica)
- Empresário → Naserv

### 1.2 Ajuste no Cadastro de Entidades
**Adicionar:**
- Campo para upload da Ficha Associativa (PDF)
- Vinculação com Profissões

### 1.3 Formas de Pagamento
**Opções:**
- Boleto Bancário (padrão)
- Consignado em Folha (específico para Governo de Pernambuco)

## 2. Integrações e APIs

### 2.1 Consulta de CEP
- Preenchimento automático de endereço
- Campos: Logradouro, Bairro, Cidade, Estado

### 2.2 Consulta de CPF
- Possibilidade de puxar nome completo
- Validação do documento

### 2.3 Sistema de Email
**Templates necessários:**
1. **Notificação de Proposta**
   - Destinatário: Cliente
   - Conteúdo: Link de acesso + Token
   - Dados dinâmicos: Nome do cliente, Nome do corretor

2. **Notificação de Pendência**
   - Destinatário: Vendedor
   - Conteúdo: Detalhes da pendência
   - Dados dinâmicos: Número da proposta, Nome do beneficiário, Tipo de pendência

### 2.4 Geração de PDF
**Requisitos:**
- Mesclar dados dinâmicos com templates fixos
- Campos em azul (preenchidos) vs texto em preto (fixo)
- Assinatura eletrônica
- Marca d'água "RASCUNHO" no preview

## 3. Regras de Negócio Importantes

### 3.1 Filtros Progressivos
Cada seleção elimina opções incompatíveis:
```
Tipo de Produto → Estado → Cidade → Profissão → Entidade → 
Abrangência → Coparticipação → Cobertura → Acomodação → 
Idade → PLANOS DISPONÍVEIS
```

### 3.2 Cálculo de Valores
- Valores devem ser calculados automaticamente baseados na faixa etária
- Exibir todas as faixas etárias no documento (transparência)
- Somar valores de todos os beneficiários (titular + dependentes)

### 3.3 Segregação de Acesso
**Vendedor NÃO pode ver:**
- Declaração de Saúde
- Respostas do cliente sobre condições médicas

**Cliente pode ver:**
- Todos os dados da proposta
- Declaração de Saúde (exclusivamente em sua etapa)

### 3.4 CPT (Cobertura Parcial Temporária)
**Trigger:** Cliente responde "SIM" em alguma pergunta de saúde
**Ação:** 
- Solicitar detalhamento (ano, condição)
- Back-office aplica CPT
- Vigência máxima: 24 meses

### 3.5 Vigências
- Sempre 3 opções disponíveis (atual + 2 próximas)
- Rotação automática quando uma fecha

## 4. Modelos de Contrato - Estrutura

### 4.1 Componentes do Documento Final
1. **Proposta de Adesão** (dados dinâmicos)
2. **Contrato** (fixo, apenas assinatura)
3. **Aditivo de Carência** (por operadora, fixo)
4. **Aditivo de Produto** (tabela de preços dinâmica)
5. **LGPD** (fixo)
6. **Manual de Orientação** (fixo)
7. **Ficha de Associação** (dados dinâmicos)
8. **Aditivos Especiais** (quando aplicável)

### 4.2 Campos Dinâmicos Necessários
**Da Proposta:**
- Todos os dados do beneficiário
- Dados dos dependentes
- Dados do corretor e corretora

**Do Sistema:**
- Tabela de preços (todas as faixas)
- Tabela de coparticipação
- Lista de municípios (para grupo de municípios)
- Valores calculados

## 5. Fluxo de Status

### 5.1 Estados da Proposta
1. **Iniciada** - Vendedor começou preenchimento
2. **Notificada** - Cliente recebeu email
3. **Em Preenchimento** - Cliente acessou
4. **Finalizada** - Cliente concluiu
5. **Em Análise** - Back-office recebeu
6. **Com Pendência** - Aguardando documentação
7. **Aprovada/Cancelada** - Status final

### 5.2 Ações por Status
- Vendedor pode acompanhar todos os status
- Vendedor pode sanar pendências (upload de novos documentos)
- Sistema deve notificar mudanças de status

## 6. Considerações de Performance

### 6.1 Otimizações Necessárias
- Cache de dados que não mudam (operadoras, planos base)
- Lazy loading para listas grandes
- Compressão de PDFs antes do upload

### 6.2 Validações em Tempo Real
- CPF
- CEP
- Email único (diferente do vendedor)
- Campos obrigatórios

## 7. Segurança

### 7.1 Tokens
- Geração única por proposta
- Validade limitada
- Hash seguro

### 7.2 Segregação de Dados
- Vendedor vê apenas suas vendas
- Cliente acessa apenas sua proposta
- Declaração de Saúde com acesso restrito

### 7.3 Logs e Auditoria
- Registrar todas as ações
- IP e timestamp
- Mudanças de status

## 8. Pontos de Atenção para Implementação

1. **Interface deve ser extremamente intuitiva** - público-alvo tem dificuldades com tecnologia
2. **Valores da tabela de preço DEVEM ser dinâmicos** - resolver problema dos 7 dias
3. **Declaração de Saúde NUNCA visível para vendedor** - crítico para compliance
4. **Upload flexível de documentos** - aceitar PDF único ou múltiplos arquivos
5. **Preview fiel ao documento final** - importante para conferência

## 9. Métricas e Relatórios Sugeridos

- Tempo médio de preenchimento por etapa
- Taxa de abandono por etapa
- Vendas por vendedor/corretora
- Pendências mais comuns
- Tempo de resolução de pendências