# Resumo Executivo - Fluxo de Venda Sistema Proposta Online

## Pontos Críticos Identificados

### 1. Interface Intuitiva é Fundamental
- Muitos vendedores são idosos ou têm dificuldades com tecnologia
- Sistema deve trabalhar com **ícones clicáveis** e evitar formulários complexos
- Cada etapa deve ser visual e autoexplicativa

### 2. Declaração de Saúde - Segregação Importante
- **NÃO deve ser visível para o vendedor** durante o processo
- Evita influência nas respostas do beneficiário
- Cliente preenche diretamente em sua etapa do processo
- Respostas positivas geram CPT (Cobertura Parcial Temporária)

### 3. Tabela de Preços Dinâmica
- **Problema atual:** PDFs estáticos que levam 7 dias para atualizar
- **Solução necessária:** Valores devem vir do sistema em tempo real
- Blocos de modelo de contrato devem ter campos dinâmicos

### 4. Cadastros Faltantes
- **Profissões:** Não existe no sistema atual
- **Vinculação Profissão-Entidade:** Relacionamento N:N
- **Formas de Pagamento:** Boleto e Consignado

## Fluxo Resumido

```
1. VENDEDOR
   ├── Login no sistema
   ├── Seleção por filtros (tipo, local, profissão, características)
   ├── Escolha do plano (valores já calculados)
   ├── Preenchimento dados do cliente
   ├── Upload documentos
   └── Notifica cliente

2. CLIENTE
   ├── Recebe email com token
   ├── Acessa sistema
   ├── Confirma dados
   ├── Preenche declaração de saúde (EXCLUSIVO)
   └── Finaliza proposta

3. BACK-OFFICE
   └── Recebe proposta para análise
```

## Ações Imediatas Necessárias

1. **Criar cadastro de Profissões**
   - Tabela simples com nome da profissão
   - Vinculação N:N com Entidades

2. **Ajustar Modelo de Contratos**
   - Implementar campos dinâmicos para tabela de preços
   - Garantir que blocos possam puxar dados do sistema

3. **Implementar Templates de Email**
   - Notificação para cliente com token
   - Notificação de pendências

4. **Garantir Segregação da Declaração de Saúde**
   - Vendedor não pode visualizar
   - Apenas cliente e back-office têm acesso

## Documentação Pendente

Pedro fornecerá:
- Manual passo a passo com prints de todas as telas
- Lista completa de profissões e entidades
- Templates de documentos e comunicações

## Considerações de UX

- **Manter navegação lateral** com indicação de passos
- **Botões grandes** e visuais claros
- **Confirmações visuais** a cada etapa
- **Preview sempre disponível** antes de finalizar