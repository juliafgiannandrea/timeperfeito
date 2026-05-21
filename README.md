# PROJETO timeperfeito

### Grupo: Anna Clara e Júlia 

### Ideia do Projeto
Aplicação interativa que permite ao usuário montar dois times a partir das convocações oficiais de 2026, simular uma partida entre eles e receber uma previsão probabilística do resultado com base nas estatísticas reais dos jogadores selecionados.

---

### Base de dados

- **Convocações 2026:** lista oficial dos jogadores convocados por cada seleção participante, com nome, posição, clube e número da camisa.

- **Estatísticas de cada jogador** de acordo com sua posição em campo:
  - https://www.transfermarkt.com.br/statistik/toptorschuetzen
  - https://api-futebol.com.br
  - https://fbref.com/en/
  - https://github.com/felipeall/transfermarkt-api 

- **Fase de Grupos**

---

### Simulação

- **Seleção dos jogadores para entrarem em campo:**
  O usuário escolhe os dois lados da partida (de partidas já definidas ou aleatórias). Para cada seleção, escolhe os 11 titulares a partir da lista de convocados. O sistema calcula automaticamente dois scores compostos para cada time:
  - **Score ofensivo** — baseado nos atacantes e meias
  - **Score defensivo** — baseado nos zagueiros e goleiro

- **Modelo probabilístico:**
  A simulação cruza os scores dos dois times usando um modelo simples e transparente:
  - A probabilidade de gol do Time A é função do seu score ofensivo contra o score defensivo do Time B.
  - O mesmo cálculo é feito no sentido inverso para o Time B.
  - O output é uma distribuição de probabilidade: % vitória A · % empate · % vitória B — e um placar mais provável sugerido.

---

### Princípios de POO

- **Classes** com métodos e atributos:
  - `Pessoa` — nome, nacionalidade, data de nascimento
  - `Jogador` — gols, interceptações, assistências, cartões amarelos, cartões vermelhos, copas jogadas, faltas, valor de mercado, time
  - `Técnico` — experiência, títulos, vitórias, derrotas
  - `Seleção` — nome, país, técnico, lista de jogadores, vitórias/derrotas, copas jogadas/ganhas
  - `Partida` — times, jogadores, resultado, data, gols, localização, estádio, horário, tipo (mata-mata ou grupo)
  - `Grupo` — times do mesmo grupo, rodadas
  - `VagaElenco` — data início e fim, jogador, seleção, posição, número do jogador, titular (boolean)
  - `Campeonato` — gerencia as partidas, quem joga com quem e pontuação para classificação

- **Herança:** `Jogador` e `Técnico` como subclasses de `Pessoa`. `Campeonato` como subclasse de `Partida`.

- **Polimorfismo:** cada tipo de jogador tem `calcularDesempenho()` diferente de acordo com sua posição.

- **Encapsulamento:** limite de cadastro de jogadores no elenco, número de camisa inválido, nacionalidade.


---
### Tecnologias que serão utilizadas (stack total):
 Toda a base de código é mantida em uma única linguagem 
- Backend: Python
- Front-end: Streamlit


