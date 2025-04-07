
# 🌐 Sistema de Cartas Trunfo Distribuído com Sockets e Pyro5

Projeto da disciplina **Sistemas Distribuídos e Paralelos**, desenvolvido com foco em comunicação entre clientes e servidor via **Sockets** (TP III) e **Pyro5** (TP IV), com arquitetura híbrida e interface em Tkinter/Pygame.

---

> 📚 Documento técnico: [`Distribuídos - TP III.pdf`](Distribuídos - TP III.pdf) e [`Distribuídos - TP IV.pdf`](Distribuídos - TP IV.pdf)
> 
> ⚠️ Projeto acadêmico com fins didáticos

## 🧠 Tecnologias Utilizadas

- `Python 3.10+`
- Sockets TCP
- `Pyro5` (Python Remote Objects)
- `SQLite3`
- `Tkinter`
- `Pygame`
- `Pillow` (PIL) para manipulação de imagens
- Threading para execução paralela
- Makefile para automação de execução

## 📦 Estrutura do Projeto

```bash
src/  
├── assets/           # Fontes e imagens para a interface  
├── controller/       # Lógica de controle (cliente e servidor)  
├── model/            # Classes de domínio (User, Deck, Card)  
├── server/           # Conexão e lógica do servidor  
├── view/             # Interface com menus e interações  
├── main1.py          # Cliente 1  
├── main2.py          # Cliente 2  
├── main3.py          # Cliente 3  
├── run_server.py     # Inicialização do servidor  
├── client.db         # Banco de dados SQLite  
├── requirements.txt  # Dependências  
└── Makefile          # Comandos utilitários  
```
---

## 🔧 Como executar

Execute o projeto com Makefile:

```
make run
```
---

## 🧱 Arquitetura

O sistema utiliza uma **arquitetura híbrida**:

- Inicialmente cliente-servidor tradicional  
- Depois, os **clientes atuam como servidores**, processando dados entre si (quase Peer-to-Peer)  
- Comunicação **bidirecional**  
- Implementações com:  🔌 Sockets (TP III) e 🔥 Pyro5 (TP IV)  

---

## 📊 Banco de Dados

Utiliza **SQLite** com estrutura normalizada:

- `cards`: cartas disponíveis no sistema  
- `client`: jogadores  
- `client_id_card_id`: cartas pertencentes a cada jogador (baralho)  
- `deck`: subconjunto de até 8 cartas para uma partida  

Na versão final:  
- Cartas podem ter **imagens personalizadas**  
- Foi implementada **serialização** com Pillow para cartas visuais  

---

## 🕹️ Mecânica do Jogo

- 3 jogadores por partida  
- Cada jogador inicia com 5 cartas do seu **deck**  
- Rodadas baseadas em atributos (ex: Inteligência, Esporte, Humor…)  
- Pontuação por rodada  
- O vencedor pode escolher uma carta da pilha de descarte  

---

## 📤 Comunicação entre Componentes

### Com Sockets (TP III):

- Mensagens personalizadas com cabeçalho  
- 4 portas por cliente: 2 envio, 2 recebimento  
- Threads independentes para envio e escuta  

### Com Pyro5 (TP IV):

- Clientes e servidor registrados no **Name Server**  
- Métodos remotos como `play_card`, `ping`, `end_game`, etc.  
- Uso de **daemon Pyro5** em threads paralelas  
- Serialização de objetos (ex: cartas) para transmissão  

---

## 🖼️ Interface Gráfica

### Tkinter (versão funcional):

- Telas para login, cadastro, edição de deck  
- Interação por botões  

### Pygame (em desenvolvimento):

- Cartas visuais com atributos  
- Menus mais bonitos e interativos  
- Componentes próprios como `Button`, `CardSelector`  

---

## 🧾 Créditos
### 👥 Autores:

- Miguel Antonio Ribeiro e Silva
- João Victor Graciano Belfort de Andrade
- Paulo Mota Gibrim

### 🏫 Universidade Federal de Viçosa – Campus Florestal
### 📚 Disciplina: Sistemas Distribuídos e Paralelos
