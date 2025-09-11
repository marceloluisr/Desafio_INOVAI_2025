# Desafio_INOVAI_2025

![pipeline_proposta](images/pipeline_proposta.png)

---

##  Requisitos de Sistema

Este projeto propõe um fluxo de execução de aprendizado de máquina para estimar medidas a partir de imagens, utilizando técnicas de visão computacional e regressão supervisionada. A seguir, são descritos os blocos de tarefas que compõem o Sprint em intervalos de dias fixos e posteriormente definimos seus requisitos funcionais com base no fluxo de execução proposto na figura acima.

---

## 🏃‍♂️ Planejamento do Sprint: 09 até 23 de setembro

### **Bloco de Tarefa 0: 09 até 11 de setembro** – *Entendimento do problema e planejamento das tarefas*
- [x] Buscar melhorias no notebook dos colaboradores **-> Eu e colaboradores**  
- [x] Entender o problema **-> Eu e colaboradores** 
- [x] Definir experimentos, métricas de avaliação e outros Blocos de Tarefas **-> Eu** 

---

### **Bloco de Tarefa 1: 11 até 13 de setembro** – *Configuração inicial e definição da baseline*
- [ ] Criar notebook para preparação dos dados **-> Colaborador B** [1°]
- [ ] Organizar a estrutura inicial do notebook **-> Eu e Colaborador B** [2°]
- [ ] Implementar código de avaliação da métrica alvo **-> Eu e Colaborador B** [3°] 
- [ ] Melhorar a qualidade das máscaras de segmentação geradas na fase Segmentação do fluxo **-> Eu e Colaborador A** [4°]
- [ ] Documentar os resultados dos experimentos da baseline  **-> Colaborador B** [5°]

---

### **Bloco de Tarefa 2: 14 até 16 de setembro** – *Desenvolvimento do Regressor no fluxo de execução proposto*
- [ ] Desenvolver código para treinar, validar e testar o regressor de estimação de medidas (alvo) **-> Eu** [6°] 
- [ ] Escrever testes unitários para o módulo do regressor **-> Colaborador A** [7°]
- [ ] Documentar os resultados experimentais **-> Colaborador B** [8°]

---

### **Bloco de Tarefa 3: 19 até 20 de setembro** – *Continuar refinamento do fluxo de execução*
- [ ] Melhorar o módulo de detecção de keypoints **-> Eu e Colaborador A** [9°]
- [ ] Avaliar e discutir o desempenho de todo o pipeline **-> Eu e colaboradores** [10°] 
- [ ] Documentar os resultados da avaliação do pipeline **-> Colaborador B** [11°]

---

### **Bloco de Tarefa 4: 21 até 23 de setembro** – *Preparar finalização*
- [ ] Revisar todos os componentes e documentações **-> Eu e Colaborador A** [12°]
- [ ] Preparar apresentação final **-> Eu e Colaborador B** [13°]

---

## Descrição e divisão de tarefas por bloco presente no fluxo de execução


1. Entrada: Dataloaders de treino, validação e teste

**Descrição:**  
Responsável por carregar os dados de entrada (imagens e labels) para os diferentes estágios do pipeline: treino, validação e teste.

**Requisitos:**
- Criar notebook para separação clara entre os conjunto de dados
- Salvar de preferência os dados de treino, validação e teste em arquivos separados como um arquivo que lista caminhos de diretórios. 

**Tarefas relacionadas:**  
Criação do notebook de preparação de dados (**Colaborador B**)  
Organização da estrutura inicial (**Colaborador B**)

---

2. Segmentação: Modelo SAM (Segment Anything Model)

**Descrição:**  
Realiza a segmentação da imagem, assumindo que a pessoa está centralizada. O modelo SAM é utilizado para gerar máscaras que destacam a região de interesse. Nesse caso, o centro da imagem é usada como prompt de ponto para realizar a segmentação da pessoa.

**Requisitos:**
- Instalar e implementar uma função para carregar a imagem de entrada, definir um ponto no centro na imagem e, por fim, gerar a máscara de segmentação.
- Verificar se deve realizar pré-processamento das imagens para compatibilidade com o modelo
- Avaliar qualidade das máscaras geradas em relação ao DeepLabV3.

**Tarefas relacionadas:**  
Melhoria da qualidade das máscaras de segmentação (**Eu**)  
Justificativa técnica será apresentada na **apresentação final**

---

3. Detecção de Keypoints: MediaPipe

**Descrição:**  
Utiliza o framework MediaPipe para detectar pontos-chave anatômicos da pessoa na imagem (ex: articulações, extremidades).

**Requisitos:**
- Integração com MediaPipe para extração de keypoints
- Tratamento de casos com detecção incompleta
- Conversão dos pontos em formato utilizável pelo Extrator de Características. Buscar criar caractéristicas geométricas baseadas nas localizações destes pontos na máscara de segmentação gerada da imagem.

**Tarefas relacionadas:**  
Testar melhoria do módulo de detecção de keypoints (**Eu**)  
Verificar se melhoria possui maior qualidade em relação à anterior presente no notebook inicial
Justificativa técnica será apresentada na **apresentação final**

---

4. Extrator de Características: Geometria dos pontos-chave

**Descrição:**  
Extrai vetores de características com base na geometria dos keypoints detectados (distâncias, ângulos, proporções).

**Requisitos:**
- Funções para cálculo geométrico entre keypoints
- Garantir compatibilidade com o modelo de regressão
- Garantir compatibilidade com a comparação com os vetores alvos verdadeiros após implementar o código de avaliação

**Tarefas relacionadas:**  
Implementar código de avaliação da métrica alvo RMSE (Root Mean Square Error) (**Eu**)  
Justificativa técnica será apresentada na **apresentação final**

---

5. Treinamento do Regressor: Random Forest

**Descrição:**  
Modelo de regressão Random Forest é treinado para estimar medidas a partir dos vetores de características extraídos.

**Requisitos:**
- Implementação do pipeline de treino, validação e teste
- Avaliação com a métrica alvo de regressão definida: RMSE (Root Mean Square Error)

**Tarefas relacionadas:**  
Desenvolvimento do regressor (**Eu**)  
Testes unitários (**Colaborador A**)  
Documentação dos resultados (**Colaborador B**)  
Justificativa técnica será apresentada na **apresentação final**

---

6. Saída: Medidas Estimadas

**Descrição:**  
O sistema retorna as medidas estimadas com base na imagem de entrada, como resultado final do fluxo de execução.

**Requisitos:**
- Garantir interface clara para visualização dos resultados
- Armazenamento dos resultados para análise posterior
- Reportar e Documentar experimentos

**Tarefas relacionadas:**  
Avaliação do pipeline (**Eu** e **Colaborador A**)  
Documentação dos resultados (**Colaborador B**)


---

# Notas sobre a organização do trabalho de colaboração no repositório

- Este projeto utiliza uma estratégia de controle centralizado de branches para garantir qualidade, organização dos módulos. As branches são nomeadas no formato: `feature/<nome-da-tarefa>-<colaborador>`. Por exemplo: `feature/dados-preparacao-b`, `feature/unitario-testes-a`, `feature/regressor-lider`

- Cada colaborador trabalha em sua própria branch, de forma paralela e independente.
- Apenas o Líder Técnico (Eu) realiza o merge para a branch principal (main), após revisão e validação.

## Descrição do processo de integração por parte dos membros colaboradores
1. O colaborador realiza commits em sua branch.
2. Abre um **Pull Request** para a branch `main`.
3. O Líder Técnico revisa, aprova e realiza o merge.
4. De modo opcional, a branch pode ser removida após integração.
