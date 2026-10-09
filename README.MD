# 🚀 Lunar Lander v3 - Deep Reinforcement Learning Benchmark

Este repositório apresenta um projeto completo de engenharia e modelagem em **Aprendizado por Reforço Profundo (Deep RL)** aplicado ao controle físico contínuo do ambiente **Lunar Lander v3** (Gymnasium). 

O objetivo principal é treinar e auditar agentes inteligentes capazes de ler telemetrias vetoriais de uma espaçonave e acionar propulsores de forma coordenada para realizar um pouso seguro na plataforma lunar.

---

## 💡 Diferenciais Técnicos do Pipeline

Ao contrário de abordagens puramente teóricas ou acadêmicas, este projeto foi desenhado sob boas práticas de engenharia de software e performance de IA:

* **Arquitetura 100% In-Memory (RAM):** O ecossistema de treinamento foi desacoplado de gravações físicas em disco. Ambientes, buffers de treino, logs e histórico de curvas de convergência são processados e mantidos estritamente na memória volátil, mantendo o ambiente de desenvolvimento limpo.
* **Estabilização de Gradiente:** Utilização de ambientes monitorados e encapsulados com wrappers de **Normalização Adaptativa de Recompensas (`VecNormalize`)** para mitigar o impacto ruidoso de spikes de pontuação (+100 por pouso / -100 por colisão).
* **Competição de Algoritmos:** Avaliação comparativa simultânea entre três grandes famílias lógicas do framework `Stable-Baselines3`: **DQN** (baseado em valor), **PPO** (baseado em gradiente de política) e **A2C** (arquitetura síncrona de Ator-Crítico).
* **Auditoria por Entropia de Shannon:** Implementação de diagnóstico matemático fina para medir a plasticidade comportamental das redes neurais após o treino, blindando o repositório contra o fenômeno de *Policy Collapse* (colapso de política onde o agente fica cego e repete o mesmo comando).

---

## 📊 Quadro Quantitativo de Resultados (300k Passos)

Após um orçamento controlado de **300.000 timesteps de interação**, os modelos foram submetidos a testes determinísticos sob sementes estocásticas independentes. O algoritmo **PPO** consagrou-se o campeão absoluto:

| Algoritmo | Recompensa Média | Desvio Padrão (Estabilidade) | Taxa de Pouso Seguro (Sucesso) | Entropia de Shannon | Status de Saúde da Política |
| :---: | :---: | :---: | :---: | :---: | :---: |
| 🏆 **PPO** | **+184.20** | **14.50** | **93.3%** | **1.91 bits** (Máx: 2.00) | ✅ Saudável e Dinâmica |
| 🥈 **A2C** | -42.10 | 38.60 | 15.0% | 1.10 bits | ⚠️ Degradação Tardia |
| 🥉 **DQN** | -125.40 | 45.10 | 0.0% | 0.32 bits | 🚨 Alerta de Colapso |

### 🧠 Perfil de Acionamento dos Motores (Modelo Campeão PPO):
* **NADA (Flutuação Inercial):** 25.5%
* **MOT_ESQ (Correção Lateral Esquerda):** 17.6%
* **MOT_DIR (Correção Lateral Direita):** 17.3%
* **MOT_PRINC (Propulsão Vertical de Frenagem):** 39.7%

---

## 🛠️ Requisitos e Instalação

O projeto utiliza exclusivamente ferramentas de código aberto (Licença MIT), eliminando dependências de ROMs proprietárias ou emuladores comerciais de terceiros. 

1. Certifique-se de ter o Python 3.10+ instalado.
2. Clone o repositório e instale as dependências contidas no arquivo `requirements.txt`:

```bash
pip install -r requirements.txt
```

### Componentes principais do arquivo `requirements.txt`:
* `gymnasium[box2d]` (Engine física de simulação contínua)
* `stable-baselines3` (Framework de algoritmos de RL)
* `torch` (Motor de processamento de Tensores/Redes Neurais)
* `tqdm`, `pandas`, `numpy`, `matplotlib`, `pygame` (Suporte, logs e renderização)

---

## 🚀 Como Executar o Projeto

O código foi estruturado de forma linear e embutida em um único Jupyter Notebook (`lunar_lander_deep_rl.ipynb`), dividido em 7 etapas sequenciais:

1. **Célula 1 - Setup:** Inicialização das bibliotecas e mapeamento de hardware.
2. **Célula 2 - O "Antes":** Demonstração inline da espaçonave caindo de forma aleatória antes do treinamento.
3. **Célula 3 - Infraestrutura:** Configuração da fábrica de vetores em memória RAM e da função de avaliação.
4. **Célula 4 - Treinamento:** Execução assíncrona do DQN, PPO e A2C controlada por barras de progresso `tqdm`.
5. **Célula 5 - Quadro de Estresse:** Geração automática do gráfico científico de convergência e do ranking do Pandas.
6. **Célula 6 - O "Depois":** Demonstração visual estabilizada e inline do modelo campeão realizando o pouso autônomo.
7. **Célula 7 - Diagnóstico:** Auditoria fina de bits de entropia de Shannon e análise preditiva de escalabilidade.

---

## ⚖️ Licença

Este repositório está sob a licença **MIT**. Sinta-se livre para clonar, estudar, modificar e distribuir o código para fins educacionais ou de portfólio.
