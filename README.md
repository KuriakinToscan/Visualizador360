# Visualizador 360° — Versão 1.1

> **Ferramenta de geração de visualizadores panorâmicos esféricos autocontidos (HTML único) para documentação de registros aéreos e processos do Sistema Eletrônico de Informações (SEI).**

---

## ⚖️ Nota de Autoria e Modificação

* **Autor e Idealizador Original:** Gilberto Milhomem Marinho Filho.
* **Modificações, Shader do Nadir e Evolução de Interface (2026):** Kuriakin Toscan.
* **Versão Atual:** 1.1 (Outubro/2026)


---

## 🎯 Objetivo

Democratizar e viabilizar a visualização de fotos panorâmicas esféricas de 360° dentro do ambiente corporativo do **SEI (Sistema Eletrônico de Informações)**. 

Imagens 360° captadas por drones (como DJI Mini, Air, Mavic, Matrice) normalmente exigem softwares especializados ou conexões externas. O **Visualizador 360°** converte essas capturas em arquivos `.html` independentes e autocontidos (com imagem, estilos, scripts e logotipo embutidos), transformando registros aéreos imersivos em **evidências documentais e probatórias natas-digitais** acessíveis a qualquer servidor ou cidadão com acesso ao processo.

---

## ✨ Novidades da Versão 1.1

A versão 1.1 consolida correções estruturais cruciais de renderização, identidade visual e compatibilidade de codificação:

1. **Eliminação da Distorção do Nadir (Solo/Polo Sul do Drone):**
   - Substituição do mapeamento UV padrão de malha facetada por **Shader Esférico Per-Pixel customizado (`THREE.ShaderMaterial` via GLSL)**.
   - Cálculo trigonométrico contínuo de direção esférica:
     $$\text{lon} = \operatorname{atan2}(x, -z), \quad \text{lat} = \operatorname{asin}(\operatorname{clamp}(y, -1.0, 1.0))$$
   - Fim do *polar pinch* (beliscão/vórtice polar) logo abaixo do drone, reproduzindo a mesma fidelidade de visualização observada nos rádios DJI (DJI RC / Fly App).
   - Filtragem bilinear pura (`THREE.LinearFilter`) sem mipmaps no shader para evitar costuras (*seams*) ou desfoque no solo.
   - Limites de inclinação vertical da câmera ampliados para **-89.9° até +89.9°** com rotação Euler `'YXZ'`.

2. **Logo Vetorial do IBAMA Embutido (Offline-First / Zero Dependências):**
   - Incorporação do logotipo oficial vetorial em formato SVG diretamente no código-fonte via Data URI Base64.
   - O gerador e todos os arquivos HTML produzidos funcionam 100% offline sem depender de requisições a imagens externas locais ou servidores de terceiros.

3. **Correção de Codificação UTF-8 e Inclusão de BOM:**
   - Correção total de caracteres acentuados da língua portuguesa (*Renováveis*, *Dimensões*, *Proporção*, *Saída*) e símbolos (`360°`, `▶`, `−`, `+`, `⟳`).
   - Inserção do **Byte Order Mark (BOM) UTF-8 (`\uFEFF`)** no Blob do gerador, garantindo que o Windows e o SEI interpretem os arquivos gerados sem erros de *mojibake*.

4. **Correção na Inicialização e Controles:**
   - Padronização dos shaders em declaração contínua de strings, prevenindo falhas de quebra de linha em navegadores legados.
   - Botão interativo de entrada `▶ Abrir visualização 360°` com transição suave e carregamento assíncrono.

---

## 🛠️ Características Técnicas

* **Arquitetura Autocontida:** Arquivo único `.html` contendo código, estilos, logo vetorial e imagem em Base64.
* **Motor Gráfico:** **Three.js (r128)** com renderização WebGL acelerada por hardware.
* **Shader Esférico Per-Pixel:** Projeção matemática equirretangular em *fragment shader*.
* **Navegação Suave e Responsiva:**
  * Interpolação suave de câmera (*lerp*).
  * Suporte híbrido completo (mouse, trackpad e gestos touch em dispositivos móveis).
  * Bússola indicadora de orientação magnética em tempo real.
  * Ajuste de campo de visão (FOV / Zoom de 30° a 110°).
  * Modo de rotação automática panorâmica.

---

## 🚀 Como Utilizar

### 1. Gerar o Visualizador 360°
1. Abra o arquivo `360_Gerador.html` em qualquer navegador moderno (Google Chrome, Microsoft Edge, Mozilla Firefox).
2. Arraste e solte a imagem panorâmica equirretangular (proporção **2:1**, preferencialmente JPG captado pelo drone).
3. Verifique as dimensões e proporção no card de metadados.
4. Digite o nome de saída desejado e clique em **"Gerar Visualizador"**.
5. Clique em **"Baixar HTML"**.

### 2. Anexar o Visualizador no SEI
1. No processo administrativo correspondente, clique em **"Incluir Documento"**.
2. Escolha o tipo de documento **"Externo"**.
3. No campo **"Tipo de Conferência / Formato"**, selecione obrigatoriamente **"Nato-digital"**.
4. No campo **"Remetente"**, preencha com a unidade ou servidor responsável.
5. Faça o upload do arquivo `.html` gerado.
6. Ao abrir o documento na árvore processual do SEI, o visualizador interativo 360° é executado diretamente na área de visualização do navegador.

---

## 💡 Dicas e Melhores Práticas

* **Resolução Recomendada para o SEI:** O SEI pode impor limites de tamanho em anexos (tipicamente entre 10 MB e 30 MB dependendo da infraestrutura do órgão). Se a foto original do drone (ex.: 8192×4096 px com ~15 MB) gerar um HTML grande demais, utilize imagens redimensionadas para 4096×2048 px ou 5376×2688 px, que mantêm altíssima nitidez visual e resultam em arquivos HTML de apenas 2 a 5 MB.
* **Proporção da Foto:** Assegure-se de que a imagem panorâmica esteja na proporção 2:1 (ex.: 8192×4096, 4096×2048), gerada pelo modo de captura panorâmica 360° / Esférica da aeronave.

---

## 📜 Licença

Este projeto é disponibilizado sob a **Licença MIT** — permitindo uso, modificação e distribuição com preservação dos créditos autorais.

---
*Tocantins — Co Yvy Ore Retama — Esta Terra É Nossa*
