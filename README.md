# Processamento Paralelo de Arquivo com Estatísticas de Localização

Este repositório contém um script em Python projetado para ler e criar um arquivo de dados (`measurements.txt`) com 500 mil registros, processá-lo em paralelo usando multiprocessamento e calcular estatísticas (mínimo, média e máximo) para cada localização encontrada nos dados gerados. Código baseado na solução de [fizmat](https://github.com/ifnesi/1brc/blob/main/calculateAverage.py), adaptado para melhor exibição das métricas e gerar um menor volume de dados.

## Funcionalidades

- Divide o arquivo em chunks para processamento paralelo.
- Usa multiprocessamento para processar os chunks de forma eficiente.
- Calcula estatísticas (mínimo, média e máximo) para cada localização nos dados.
- Apresenta os resultados finais em formato legível.

## Requisitos

- Python 3.x
- Biblioteca `multiprocessing` (já incluída na biblioteca padrão do Python)

## Uso
1. **Clonar o Repositório**
   ```bash
   git clone https://github.com/JacksonAguiar/1brc-challenge.git
   cd 1brc-challenge

1. **Instalar as dependências**
   ```bash 
   pip install -r requirements.txt

2. **Gerar o arquivo**
   ```bash
   python3 generateFile.py

3. **Calcular as métricas**
   ```bash
   python3 calculate.py


## Detalhe das tecnicas utilizadas

### Chunks e processamento paralelo
A divisão do arquivo em chunks é essencial para lidar com grandes conjuntos de dados de forma eficiente. Ao dividir o arquivo em partes menores, chamadas de chunks, podemos processar cada parte de forma independente e paralela. Isso permite uma melhor utilização dos recursos do sistema, especialmente ao distribuir o trabalho entre múltiplos núcleos de CPU. No código apresentado, a divisão em chunks é feita com base no tamanho ideal de cada chunk, considerando o número de CPUs disponíveis ou um número máximo especificado (max_cpu). A escolha de limites naturais, como quebras de linha, garante que cada chunk comece e termine em pontos apropriados, preservando a integridade dos dados.

### Multiprocessamento
O multiprocessamento é uma técnica que envolve a execução simultânea de múltiplos processos em paralelo, aproveitando os recursos do hardware disponível. No contexto do processamento de chunks, o multiprocessamento permite que diferentes partes do arquivo sejam processadas ao mesmo tempo, reduzindo significativamente o tempo total de processamento. No código fornecido, a biblioteca multiprocessing é usada para criar um pool de processos(mp.Pool) que coordena a execução dos processos paralelos. Cada processo no pool é responsável por processar um chunk específico do arquivo de forma independente e eficiente, contribuindo para um processamento mais rápido e escalável de grandes volumes de dados.