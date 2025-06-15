# Projeto DDDA AI Voice Dubbing (PT-BR)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
Este é um projeto inovador que explora o potencial da **Inteligência Artificial (IA)** para criar novas dublagens em **Português do Brasil (PT-BR)** para os icônicos personagens do aclamado RPG de ação, **Dragon's Dogma: Dark Arisen (DDDA)**.

Nosso objetivo principal é demonstrar como a IA pode ser utilizada para gerar vozes de alta qualidade, mantendo a essência e o tom dos áudios originais do jogo.

---

## 🎯 Motivação e Objetivos

A paixão por Dragon's Dogma: Dark Arisen e o fascínio pelas capacidades emergentes da Inteligência Artificial impulsionaram a criação deste projeto. Nossos objetivos incluem:

* **Explorar as fronteiras da síntese de voz por IA:** Aplicar tecnologias de ponta na geração de áudio vocal.
* **Enriquecer a experiência de DDDA:** Oferecer uma nova perspectiva sonora para fãs, com dublagens em PT-BR.
* **Demonstrar o potencial da IA na dublagem:** Criar um showcase funcional das possibilidades da IA no entretenimento.
* **Fomentar a comunidade:** Criar um ambiente para colaboração e aprendizado sobre IA e processamento de áudio.

---

## 💻 Tecnologia Utilizada

Este projeto é construído sobre uma base robusta de tecnologias de Machine Learning e processamento de áudio:

* **Linguagem de Programação:** Python
* **Frameworks de IA:** PyTorch / TensorFlow (a escolha final dependerá do modelo de IA selecionado)
* **Biblioteca de Síntese/Conversão de Voz:** `[Nome da Biblioteca de IA/Modelo - Ex: Coqui TTS, RVC (Retrieval-based Voice Conversion), Bark, XTTS etc.]` - *Este será o foco da pesquisa e implementação inicial.*
* **Aceleração por Hardware:** CUDA (para GPUs NVIDIA) é essencial para um treinamento e inferência eficientes dos modelos de IA.

---

## ⚙️ Como o Projeto Funciona (Visão Geral)

O processo básico para gerar as dublagens envolve as seguintes etapas:

1.  **Coleta de Áudio Original:** Extração e isolamento das falas dos personagens de Dragon's Dogma: Dark Arisen.
2.  **Preparação de Dados (Dataset):** Limpeza, normalização e formatação dos áudios e seus respectivos transcrições para treinamento do modelo de IA.
3.  **Treinamento do Modelo de IA:** A Inteligência Artificial aprende os padrões vocais, entonação, emoções e timbre a partir dos áudios originais.
4.  **Geração de Vozes (Inferência):** Com base em novos textos (roteiros de dublagem em PT-BR) e a voz "aprendida" do personagem, a IA sintetiza as novas falas.
5.  **Pós-Processamento e Integração:** Realização de ajustes finos (como mixagem, equalização) e preparação das dublagens para apresentação e possível integração em mods futuros.

---

## ⏳ Status do Projeto e Próximos Passos

O projeto está atualmente na **fase inicial de configuração do ambiente e pesquisa de modelos**. Nossa roadmap para as próximas etapas inclui:

* **Finalização da Configuração do Ambiente:** Garantir que todas as dependências e ferramentas estejam prontas para o desenvolvimento.
* **Pesquisa e Seleção do Modelo/Biblioteca de IA:** Avaliar e escolher a tecnologia de síntese/conversão de voz mais adequada para os objetivos do projeto.
* **Coleta e Preparação do Dataset:** Montagem e organização do conjunto de dados de áudio de Dragon's Dogma: Dark Arisen.
* **Treinamento do Modelo de IA:** Iniciar o processo de treinamento com o dataset preparado.
* **Geração das Primeiras Amostras de Dublagem:** Produzir os primeiros exemplos das vozes geradas por IA.
* **Criação da Página de Demonstração (GitHub Pages):** Desenvolver o showcase interativo para apresentar os resultados do projeto.

---

## 🚀 Setup do Ambiente de Desenvolvimento

Para contribuir ou testar o projeto localmente, siga os passos abaixo para configurar seu ambiente. Se você utiliza um sistema Linux baseado em OSTree (como o **Bazzite**), recomendamos fortemente o uso de **Distrobox** para garantir um ambiente de desenvolvimento isolado e robusto.

### Pré-requisitos

* **Git:** Para clonar o repositório.
* **Docker ou Podman:** Ferramentas de contêiner (geralmente já vêm instaladas ou são dependências do Distrobox).
* **Para usuários Linux Bazzite/OSTree:** [Distrobox](https://distrobox.priv.pw/) (instale via `sudo rpm-ostree install distrobox` se ainda não tiver, e reinicie).
* Uma **GPU NVIDIA** é **altamente recomendada** para um desempenho aceitável no treinamento e inferência dos modelos de IA. Certifique-se de que seus drivers NVIDIA estejam instalados e funcionando corretamente no sistema host.

### Passos para Configuração (com Distrobox - Recomendado para Bazzite)

1.  **Criar e Entrar no Contêiner Distrobox:**
    Utilize um ambiente como Ubuntu 22.04 (LTS) ou Fedora, que possuem vasta documentação e compatibilidade com bibliotecas de Machine Learning.
    ```bash
    distrobox create --name ddda-ai-dev --image ubuntu:22.04 # Ou 'fedora:latest' para Fedora
    distrobox enter ddda-ai-dev
    ```
    *Se você não estiver usando Bazzite ou preferir um ambiente virtual Python tradicional em uma distro Linux normal, pule os passos do Distrobox e use `python3 -m venv .venv` e `source .venv/bin/activate`.*

2.  **Dentro do Contêiner: Instalar Dependências Básicas:**
    ```bash
    # Para contêiner Ubuntu/Debian:
    sudo apt update && sudo apt upgrade -y
    sudo apt install python3 python3-pip git -y

    # Para contêiner Fedora (se optou por ele):
    # sudo dnf update -y
    # sudo dnf install python3 python3-pip git -y
    ```

3.  **Configurar Aceleração por GPU (NVIDIA CUDA/cuDNN):**
    Este é o passo mais crítico para o desempenho. As instruções exatas dependem do framework de IA (PyTorch ou TensorFlow) e da versão específica do CUDA que o modelo de IA escolhido exige. **Consulte a documentação oficial da biblioteca de IA que você planeja usar.** Geralmente, envolve a adição de repositórios específicos e a instalação do CUDA Toolkit e do cuDNN **dentro do seu contêiner**.

4.  **Clonar o Repositório:**
    ```bash
    git clone [https://github.com/](https://github.com/)<SEU_USUARIO_GITHUB>/DDDA-AI-VOICE-DUBBING-PT-BR.git
    cd DDDA-AI-VOICE-DUBBING-PT-BR
    ```

5.  **Instalar Dependências do Projeto:**
    Após decidir e configurar seu modelo de IA, você instalará as bibliotecas Python necessárias.
    ```bash
    # Se houver um arquivo 'requirements.txt' no futuro:
    # pip install -r requirements.txt

    # Exemplo genérico (ajuste conforme o modelo de IA e versão do CUDA):
    # pip install torch torchvision torchaudio --index-url [https://download.pytorch.org/whl/cu118](https://download.pytorch.org/whl/cu118) # Para PyTorch com CUDA 11.8
    # pip install [nome-da-biblioteca-de-ia-escolhida]
    ```

### Observação Importante sobre a Escolha do Modelo de IA

As instruções detalhadas de instalação e uso para a **biblioteca de síntese/conversão de voz (ex: RVC, Coqui TTS, Bark, XTTS)** serão adicionadas aqui assim que um modelo for selecionado e testado em fase de desenvolvimento. Este é um passo fundamental que impactará as dependências exatas e o fluxo de trabalho.

---

## 🎧 Exemplos de Dublagens

*Em breve, esta seção conterá amostras de áudio das dublagens geradas por IA, demonstrando o progresso do projeto e a qualidade dos resultados.*

*Para uma experiência interativa e para ouvir as últimas amostras, visite nossa [Página do GitHub Pages](https://<SEU_USUARIO_GITHUB>.github.io/DDDA-AI-VOICE-DUBBING-PT-BR/).*

---

## 🤝 Como Contribuir

Sua contribuição é muito bem-vinda! Se você tem interesse em IA, Machine Learning, processamento de áudio, ou é apenas um fã de Dragon's Dogma, veja como pode ajudar:

1.  Faça um fork deste repositório.
2.  Crie uma branch para sua feature (`git checkout -b feature/minha-nova-feature`).
3.  Commit suas mudanças (`git commit -m 'Adiciona uma nova feature'`).
4.  Envie para a branch (`git push origin feature/minha-nova-feature`).
5.  Abra um Pull Request, descrevendo suas mudanças.

Por favor, leia nosso [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md) para garantir uma comunidade respeitosa e inclusiva.

---

## 📄 Licença

Este projeto está sob a licença **MIT License**. Veja o arquivo [LICENSE.md](LICENSE.md) para mais detalhes.

---

## ✉️ Contato

Para dúvidas, sugestões ou colaborações, sinta-se à vontade para abrir uma [Issue neste repositório](https://github.com/<SEU_USUARIO_GITHUB>/DDDA-AI-VOICE-DUBBING-PT-BR/issues) ou entrar em contato através de:

* **Email:** `[seu_email@example.com]`
* **LinkedIn:** `[Link para o seu perfil no LinkedIn]`
* **Twitter/X:** `[Link para o seu perfil no Twitter/X]`

---
