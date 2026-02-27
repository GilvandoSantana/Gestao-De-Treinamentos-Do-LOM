# Brainstorm de Design — Gestão de Treinamentos

## Contexto
Sistema de gestão de treinamentos de colaboradores industriais. Funcionalidades: CRUD de colaboradores, controle de treinamentos com validade, filtros por status (válido, próximo a vencer, vencido), importação/exportação de dados JSON. Público-alvo: supervisores e técnicos de segurança em ambiente industrial.

---

<response>
## Ideia 1 — Industrial Blueprint

<text>
**Design Movement:** Neo-Industrial / Technical Blueprint

**Core Principles:**
1. Clareza funcional — cada elemento tem propósito claro, sem decoração supérflua
2. Hierarquia visual forte — uso de peso tipográfico e cor para guiar o olhar
3. Robustez visual — transmite confiança e seriedade, condizente com segurança industrial
4. Densidade informacional controlada — muita informação, mas bem organizada

**Color Philosophy:** Paleta baseada em azul-marinho profundo (#1a2332) como cor principal, representando confiança e autoridade. Acentos em laranja industrial (#e8772e) para ações e alertas, verde petróleo (#2d9f7f) para status positivo, e vermelho sinalização (#d94052) para urgência. Fundo em cinza claro quente (#f4f1ed) que evita a frieza do branco puro.

**Layout Paradigm:** Layout de painel de controle com sidebar fixa à esquerda contendo navegação e estatísticas. Área principal com grid assimétrico — cards de colaboradores em formato de "fichas técnicas" com borda esquerda colorida indicando status.

**Signature Elements:**
1. Borda lateral colorida nos cards indicando status do treinamento (semáforo visual)
2. Badges com ícones de segurança industrial (capacete, escudo, certificado)
3. Micro-animações de "stamp" ao salvar/confirmar ações

**Interaction Philosophy:** Interações diretas e confirmativas. Cada ação importante tem feedback visual imediato — toasts informativos, transições suaves de estado. Modal de formulário desliza da direita como um painel lateral.

**Animation:** Transições de 200-300ms com easing cubic-bezier. Cards entram com fade-in escalonado. Badges de status pulsam suavemente quando próximos a vencer. Botões têm micro-escala no hover (1.02).

**Typography System:** 
- Display: "Plus Jakarta Sans" Bold (títulos e números grandes)
- Body: "Plus Jakarta Sans" Regular/Medium (texto corrido e labels)
- Mono: Para datas e códigos
</text>
<probability>0.08</probability>
</response>

---

<response>
## Ideia 2 — Safety Dashboard Moderno

<text>
**Design Movement:** Flat Design Refinado com toques de Glassmorphism

**Core Principles:**
1. Acessibilidade cromática — cores de status universalmente reconhecíveis
2. Espaçamento generoso — interface respirável mesmo com muitos dados
3. Feedback visual rico — cada interação é acompanhada de resposta visual
4. Responsividade nativa — funciona igualmente bem em tablet e desktop

**Color Philosophy:** Base em slate escuro (#0f172a) com superfícies em tons de slate (#1e293b, #334155). Texto em branco e cinza claro. Cores de status vibrantes contra fundo escuro: esmeralda (#10b981) para válido, âmbar (#f59e0b) para atenção, rosa-vermelho (#f43f5e) para vencido. Acentos em azul elétrico (#3b82f6) para ações primárias.

**Layout Paradigm:** Layout vertical fluido com header fixo contendo barra de busca e ações rápidas. Dashboard de estatísticas no topo com cards glassmorphism. Grid responsivo de 1-3 colunas para cards de colaboradores. Filtros como tabs horizontais com indicador animado.

**Signature Elements:**
1. Cards com efeito glassmorphism sutil (backdrop-blur + transparência)
2. Indicadores de progresso circulares para percentual de treinamentos válidos por colaborador
3. Gradientes sutis nos headers dos cards de colaborador

**Interaction Philosophy:** Interface escura e imersiva. Hover revela ações secundárias. Modais com overlay blur. Transições fluidas entre estados de filtro. Drag-and-drop para reordenar (futuro).

**Animation:** Framer Motion para entrada de cards (stagger de 50ms). Transições de filtro com layout animation. Números de estatísticas com contagem animada. Modais com spring animation.

**Typography System:**
- Display: "Outfit" SemiBold/Bold (títulos e métricas)
- Body: "Outfit" Regular/Medium (texto e labels)
- Hierarquia: 4xl para métricas, 2xl para títulos de seção, base para conteúdo
</text>
<probability>0.06</probability>
</response>

---

<response>
## Ideia 3 — Clean Corporate Safety

<text>
**Design Movement:** Swiss Design Contemporâneo / Corporate Minimal

**Core Principles:**
1. Grid rigoroso — alinhamento perfeito cria ordem visual
2. Tipografia como elemento principal — hierarquia clara sem depender de decoração
3. Cor com propósito — cada cor tem significado funcional específico
4. Simplicidade operacional — interface que não distrai, focada na tarefa

**Color Philosophy:** Fundo branco puro com superfícies em cinza muito claro (#f8fafc). Texto principal em cinza escuro (#1e293b). Cor primária em índigo profundo (#4338ca) para ações e identidade. Sistema de cores de status: verde floresta (#059669) para válido, amarelo mostarda (#d97706) para atenção, vermelho tijolo (#dc2626) para vencido. Bordas sutis em cinza (#e2e8f0).

**Layout Paradigm:** Layout de página única com scroll vertical. Header compacto com título e ações alinhados. Barra de estatísticas horizontal. Filtros como chips/pills. Cards em grid de 3 colunas com espaçamento generoso. Formulário em dialog centralizado com overlay.

**Signature Elements:**
1. Tags de status com ícone + texto em cápsulas coloridas
2. Separadores visuais com linhas finas e espaçamento amplo
3. Cantos arredondados consistentes (12px) em todos os containers

**Interaction Philosophy:** Minimalista e previsível. Hover sutil com elevação de sombra. Foco visível para acessibilidade. Confirmações via dialog, não alerts nativos. Feedback via toasts discretos.

**Animation:** Transições CSS puras de 150-250ms. Hover com translate-y(-2px) e sombra expandida. Modais com fade + scale sutil. Sem animações complexas — velocidade e clareza.

**Typography System:**
- Display: "DM Sans" Bold (títulos)
- Body: "DM Sans" Regular/Medium (conteúdo)
- Hierarquia baseada em peso e tamanho, sem itálico
</text>
<probability>0.07</probability>
</response>
