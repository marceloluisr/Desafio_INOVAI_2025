# Instruções

Reomendo executar os notebooks no Google Colab. Faça uma cópia destes notebooks e execute nesta sequência:


1) notebooks/preparacao_analise.ipynb: para preparacao dos arquivos de carregamento dos dados para cada tipo de split. Executado somente uma vez.
>  [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/marceloluisr/Desafio_INOVAI_2025/blob/main/src/notebooks/preparacao_analise.ipynb)

 2) notebooks/modelagem_treinamento.ipynb: essencialmente para treinamento dos regressores.
  >  [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/marceloluisr/Desafio_INOVAI_2025/blob/main/src/notebooks/modelagem_treinamento.ipynb)


 3) notebooks/avaliacao.ipynb: para avaliação do desempenho do sistema com dados de validação e teste.
  > [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/marceloluisr/Desafio_INOVAI_2025/blob/main/src/notebooks/avaliacao.ipynb)

Baixe o arquivo u2net_human_seg.pth de pesos da U2Net neste link abaixo e depois altere o caminho para o arquivo  no arquivo de configuração  **configuration.yaml**, especificamente na chave "u2net_seg_human_model_path'. 

> https://drive.google.com/file/d/1m_Kgs91b21gayc2XLW0ou8yugAIadWVP/view
