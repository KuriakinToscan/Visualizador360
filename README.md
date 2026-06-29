# Visualizador 360º
### Visualizador Esférico 360° 

O **Visualizador360** é uma ferramenta desenvolvida para suprir a lacuna de suporte nativo a imagens esféricas no Sistema Eletrônico de Informações (SEI). Ele permite converter imagens 360° captadas por drones em arquivos HTML autocontidos, onde a imagem é embutida via Base64, garantindo que o registro possa ser visualizado em qualquer navegador sem dependência de internet ou softwares externos.

---

## ⚖️ Nota de Autoria e Modificação
**Este projeto é uma versão modificada e aprimorada a partir do código original.**

* **Autor e Idealizador Original:** Gilberto Milhomem Marinho Filho.
* **Modificações e Evolução de Interface (2026):** Kuriakin Toscan.
* **Aprimoramento e Novas Funcionalidades (EXIF, campo descrição, 2026):** Luiz Augusto - (github.com/laoc81).
* **Instituição:** IBAMA — Instituto Brasileiro do Meio Ambiente e dos Recursos Naturais Renováveis.
* **Unidade de Origem:** DIPAM-TO — Divisão de Proteção Ambiental do Tocantins.

---

## 🎯 Objetivo
Democratizar a visualização de imagens 360° dentro do ambiente SEI, transformando registros aéreos imersivos em evidências documentais acessíveis a qualquer servidor público com acesso ao processo.

## 🛠️ Características Técnicas
* **Arquitetura Zero Dependências:** O visualizador gerado é autossuficiente e funciona em máquinas offline.
* **Motor de Renderização:** Utiliza a biblioteca **Three.js (r128)** para projeção esférica via WebGL.
* **Alta Fidelidade:** Esfera configurada com 96×64 segmentos para minimizar distorções nos polos da imagem.
* **Navegação Suave:** Implementação de interpolação de movimento (lerp) para evitar saltos bruscos no arraste.
* **Leitura de EXIF:** Integração com a biblioteca `exif-js` para extração automática de metadados diretamente no navegador.
* **Extração automática de metadados EXIF** – ao carregar a imagem, o sistema lê e exibe:
  - Modelo do drone utilizado;
  - Data e hora da captura;
  - Coordenadas GPS (latitude/longitude);
- **Campo de descrição personalizável** – o usuário pode adicionar um texto descritivo que será exibido no cabeçalho do visualizador gerado, substituindo o texto padrão "IBAMA · INSPEÇÃO AMBIENTAL".
- **Metadados embutidos no HTML final** – todas as informações extraídas são inseridas automaticamente no cabeçalho do arquivo gerado, documentando a origem da imagem.

## 🚀 Como Utilizar

### 1. Gerar o Visualizador
1.  Abra o arquivo `360_Gerador.html` no Google Chrome ou Microsoft Edge.
2.  Arraste a sua imagem 360° (proporção 2:1) para a área indicada.
3.  Confira os metadados e o nome de saída.
4.  **(Opcional)** Preencha o campo **"Descrição"** com um texto personalizado que aparecerá no cabeçalho do visualizador gerado. Caso deixe em branco, será usado o padrão `"IBAMA · INSPEÇÃO AMBIENTAL"`
5.  Clique em **"Gerar Visualizador 360°"** e baixe o arquivo HTML final.

### 2. Anexar no SEI
1.  No processo desejado, selecione **"Incluir Documento"** e escolha a opção **"Externo"**.
2.  No campo "Formato", selecione obrigatoriamente **"Nato-digital"**.
3.  Faça o upload do arquivo HTML gerado.
4.  Ao clicar no documento na árvore do processo, o SEI abrirá o visualizador interativo diretamente no navegador.

## ⚠️ Solução de Problemas
* **Imagem Distorcida:** Verifique se a foto original foi captada no modo "Esférico/Panorâmico" do drone (proporção 2:1).
* **Arquivo Muito Grande para o SEI:** O limite prático de upload costuma ser de 5 a 8 MB. Se necessário, redimensione a imagem original para 4096×2048 px antes de processar no gerador.
* **Tela Preta no Visualizador:** Pode indicar que a biblioteca Three.js não foi carregada devido a bloqueios de rede no domínio da CDN.

## 🤝 Como Contribuir
Contribuições são bem-vindas! Para propor melhorias, correções ou novas funcionalidades:
1. **Faça um fork** deste repositório.
2. **Crie uma branch** para sua alteração (`git checkout -b minha-melhoria`).
3. **Faça as alterações** e commit (`git commit -m "feat: descrição da melhoria"`).
4. **Envie para o seu fork** (`git push origin minha-melhoria`).
5. **Abra um Pull Request** descrevendo claramente o que foi alterado e por quê.

Agradecemos antecipadamente por sua colaboração!


## 📜 Licença
Este projeto é distribuído sob a **Licença MIT**.


