# Prompt — App Família Furtado

## Contexto

Crie um aplicativo web completo em **React (JSX)** chamado **"Família Furtado"**, destinado à organização pessoal e familiar. O app deve ser mobile-first, com navegação por abas na parte inferior da tela, tema dark (fundo `#0a0a1a`), tipografia elegante com `Playfair Display` (títulos) e `DM Sans` (corpo), e paleta de cores baseada em rosa `#e85d96` como cor principal.

Todos os dados devem persistir via `localStorage`. Não utilizar `<form>` HTML — usar apenas `onClick` e `onChange`.

---

## Membros Iniciais

Pré-cadastrar os seguintes membros com cores distintas:

| Nome | Função | Cor |
|---|---|---|
| Carla Furtado | Mãe / Responsável | `#e85d96` |
| Vanessa | Cônjuge | `#8b5cf6` |
| Lívia | Filha | `#f59e0b` |
| Giovanna | Filha | `#10b981` |

---

## Estrutura de Navegação (Bottom Tab Bar)

7 abas fixas na parte inferior:

1. **Início** — Dashboard geral
2. **Família** — Cadastro dos membros
3. **Tarefas** — Lista de afazeres
4. **Agenda** — Eventos coletivos e individuais
5. **Lembretes** — Alertas com data, hora e repetição
6. **Compras** — Listas separadas por local
7. **Medidas** — Tamanhos e medidas dos membros

---

## Seção 1 — Início (Dashboard)

- Saudação dinâmica por horário (Bom dia / Boa tarde / Boa noite) com o nome "Carla"
- Avatares dos membros no cabeçalho (inicial do nome com a cor do membro)
- 4 cards de resumo em grid 2x2:
  - Tarefas pendentes
  - Eventos próximos
  - Lembretes ativos
  - Itens de compras pendentes
- Cada card é clicável e navega para a seção correspondente
- Grid de atalhos rápidos para todas as seções
- Bloco de alerta amarelo exibindo lembretes do dia atual (se houver)

---

## Seção 2 — Família (Cadastro)

Campos por membro:
- Nome completo
- Função / Parentesco (ex.: Filha, Cônjuge)
- Telefone
- E-mail
- Modelo do celular
- **Medidas:** Cintura (cm), Quadril (cm), Busto (cm), Altura (cm), Calça (tamanho), Blusa/Vestido (tamanho), Calçado (número)
- Cor personalizável (color picker)

Funcionalidades:
- Botão "Adicionar" para novo membro
- Editar e excluir membros (exceto o membro de id fixo 1)
- Card visual por membro com avatar colorido, badges de função e exibição das medidas preenchidas
- Modal para criação/edição

---

## Seção 3 — Tarefas

Categorias disponíveis: `Fazer`, `Não Esquecer`, `Lembrar`, `Urgente`, `Pessoal`, `Trabalho`

Campos por tarefa:
- Título
- Categoria (select)
- Prioridade: `Urgente`, `Alta`, `Normal`, `Baixa` (com cores distintas: vermelho, amarelo, índigo, verde)
- Responsável (select com membros cadastrados)
- Data limite (date picker)
- Observação/Nota

Funcionalidades:
- Filtro por categoria (pills clicáveis)
- Marcar como concluída (checkbox com animação)
- Excluir tarefa
- Contador de pendentes no título da seção
- Itens concluídos ficam com 50% de opacidade e riscados

---

## Seção 4 — Agenda

Tipos de agenda: `Coletiva` (família toda) e `Individual` (por membro)

Campos por evento:
- Título
- Data e Horário
- Tipo (coletiva / individual)
- Participante principal (select com membros)
- Observações (local, detalhes)
- **Checkbox "Abrir no Google Agenda ao salvar":** ao marcar e salvar, gera URL do Google Calendar com os dados e abre em nova aba

Funcionalidades:
- Filtro por tipo (Coletiva / Individual) com botões
- Filtro por membro (select)
- Separação visual: "Próximos Eventos" e "Anteriores"
- Card de evento com mini-calendário (mês + dia) na cor do membro
- Excluir evento

**URL Google Agenda:**
```
https://calendar.google.com/calendar/render?action=TEMPLATE
  &text={título}
  &dates={startISO}/{endISO}
  &details={observações}
```
Duração padrão: 1 hora. Horário padrão se não preenchido: 09:00.

---

## Seção 5 — Lembretes

Campos por lembrete:
- Texto do lembrete
- Data e Horário
- Para quem (select: "Família toda" ou membro específico)
- Prioridade: `Urgente`, `Alta`, `Normal`, `Baixa`
- Repetição: `Não repete`, `Diário`, `Semanal`, `Mensal`, `Anual`

Funcionalidades:
- Bloco de aviso amarelo no topo da seção listando lembretes do dia atual não concluídos
- Marcar como concluído (checkbox circular)
- Excluir lembrete
- Ordenação por data (mais próximos primeiro)
- Itens concluídos com opacidade reduzida e riscados

---

## Seção 6 — Lista de Compras

Listas separadas por local (abas com ícone emoji):

| Lista | Ícone |
|---|---|
| Mercado | 🛒 |
| Casa Praia | 🏖️ |
| Casa Caxias | 🏠 |
| Farmácia | 💊 |
| Vestuário | 👗 |
| Outros | 📦 |

Campos por item:
- Quantidade (campo curto à esquerda)
- Nome do item (campo principal)

Funcionalidades:
- Adicionar item via botão ou tecla Enter
- Marcar item como comprado (checkbox)
- Excluir item
- Botão "Limpar itens marcados" (aparece quando há itens concluídos)
- Badge com contador de pendentes por lista
- Contador global no título: "X de Y itens pendentes"

---

## Seção 7 — Medidas & Tamanhos

- Seletor de membro no topo (pills com a cor de cada membro)
- Grid 2x2 com cards para cada medida do membro selecionado:
  - 📏 Cintura (cm)
  - 📏 Quadril (cm)
  - 📏 Busto (cm)
  - 📐 Altura (cm)
  - 👖 Calça (tamanho)
  - 👕 Blusa / Vestido (tamanho)
  - 👟 Calçado (número)
- Campos sem valor exibem "Não informado" em itálico
- Campos preenchidos destacados com borda na cor do membro

**Guia de Tamanhos BR** (bloco informativo no rodapé da seção):

Calça:
`34→68-72cm` | `36→72-76cm` | `38→76-80cm` | `40→80-84cm` | `42→84-88cm` | `44→88-92cm` | `PP→até 72cm` | `P→72-76cm` | `M→76-80cm` | `G→80-88cm` | `GG→88-96cm`

Blusa/Vestido:
`PP→Busto 80-84cm` | `P→84-88cm` | `M→88-92cm` | `G→92-98cm` | `GG→98-104cm` | `XGG→104-110cm`

O tamanho do membro selecionado é destacado com a cor do membro.

---

## Componentes Reutilizáveis

### `<Modal title onClose>`
- Overlay escuro semi-transparente
- Card centralizado com borda `#2d2d4e`, borderRadius 16px, fundo `#1a1a2e`
- Cabeçalho com título e botão X
- Scroll interno (`overflow: auto`, `maxHeight: 90vh`)

### `<FInput label value onChange type placeholder>`
- Label em uppercase, letra pequena, cor `#aaa`
- Input com fundo `#0d0d1a`, borda `#2d2d4e`, cor branca

### `<FSelect label value onChange options>`
- Mesmo visual do FInput

### `<Badge text color>`
- Pill com fundo `color + "22"`, borda `color + "44"`, texto na cor

### `<Icon name size>`
- SVG inline com paths para: `home`, `users`, `calendar`, `bell`, `shopping`, `ruler`, `check`, `plus`, `trash`, `edit`, `x`, `clock`, `link`, `person`, `tag`, `task`, `warn`, `phone`, `mail`, `map`, `star`

---

## Hook de Persistência

```js
const useStorage = (key, initialValue) => {
  const [val, setVal] = useState(() => {
    try {
      const stored = localStorage.getItem(key);
      return stored ? JSON.parse(stored) : initialValue;
    } catch { return initialValue; }
  });
  useEffect(() => {
    try { localStorage.setItem(key, JSON.stringify(val)); } catch {}
  }, [key, val]);
  return [val, setVal];
};
```

Chaves usadas:
- `ff_members` — membros da família
- `ff_tasks` — tarefas
- `ff_events` — eventos da agenda
- `ff_reminders` — lembretes
- `ff_shopping` — listas de compras (objeto com chave por lista)

---

## Design System

```
Fundo principal:      #0a0a1a
Fundo card:           #12122a
Fundo input:          #0d0d1a
Fundo item:           #1a1a2e
Borda padrão:         #1e1e3a
Borda sutil:          #2d2d4e

Rosa principal:       #e85d96
Índigo:               #6366f1
Âmbar:                #f59e0b
Verde:                #10b981
Vermelho:             #ef4444

Texto principal:      #ffffff
Texto secundário:     #aaaaaa
Texto desativado:     #555555

Título (serif):       Playfair Display 600–800
Corpo (sans):         DM Sans 400–700
```

---

## Comportamentos Adicionais

- Saudação dinâmica: antes das 12h → "Bom dia", 12–18h → "Boa tarde", após 18h → "Boa noite"
- Aviso de lembretes do dia visível tanto no Dashboard quanto na seção de Lembretes
- Eventos passados exibidos com opacidade 60%, apenas os 5 mais recentes
- Tarefas e lembretes concluídos ficam visíveis mas com opacidade 50% e texto riscado
- Bottom nav fixa com ícone e label, cor `#e85d96` quando ativo, `#444` quando inativo
- Google Fonts carregado via `<link>` dentro do JSX retornado
