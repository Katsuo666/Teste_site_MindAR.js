========================================================================
             PROJETO TESTE: MindAR.js (Rastreio de Imagem)
========================================================================

1. DESCRIÇÃO GERAL
------------------
Este projeto consiste num teste de Conceito (PoC) de Realidade Aumentada
baseada na Web (WebAR) utilizando a biblioteca MindAR.js. 
A solução permite reconhecer uma ilustração/imagem impressa no livro físico 
(Image Tracking) e projetar sobre ela o modelo 3D correspondente, sem necessidade 
de marcadores pretos com molduras.

2. ESTRUTURA DE FICHEIROS
-------------------------
/ (Raiz do Projeto)
│
├── index.html               # Ficheiro principal com a cena A-Frame / MindAR
├── README.txt               # Documentação técnica do projeto
└── assets/
    ├── 02_Bolsos.mind       # Ficheiro compilado com os alvos de imagem (Targets)
    └── 02_Bolsos.glb        # Modelo 3D no formato GLTF/GLB

3. TECNOLOGIAS E DEPENDÊNCIAS
-----------------------------
- HTML5 / CSS3 / JavaScript (ES6)
- A-Frame v1.4.2 (Motor 3D Web)
- MindAR.js v1.2.5 (Biblioteca de Image Tracking para A-Frame)
- A-Frame Extras v6.1.1 (Para suporte a animações 3D / animation-mixer)

4. CONFIGURAÇÕES TÉCNICAS E SOLUÇÃO DE PROBLEMAS
------------------------------------------------
- Resolução do Pivot e Escala:
  O modelo '02_Bolsos.glb' utiliza a escala calibrada '15 15 15' diretamente na tag 
  <a-gltf-model>, anulando a necessidade de scripts complexos de auto-centragem.
- Correção de Cor e Iluminação:
  Para evitar que o modelo 3D apareça transparente ou escuro no ecrã, a tag <a-scene> 
  inclui as propriedades:
  color-space="sRGB"
  renderer="colorManagement: true, physicallyCorrectLights: true"
- Controlo de Câmara:
  Uso de <a-camera position="0 0 0" look-controls="enabled: false"></a-camera> para 
  garantir que a câmara virtual fica bloqueada e alinhada com o feed de vídeo.

5. COMO EXECUTAR
----------------
1. Devido às restrições de segurança do browser relativamente ao acesso à câmara 
   (MediaDevices Web API), este projeto exige ser servido num ambiente HTTPS ou 
   num servidor local seguro.
2. Aceder via browser móvel (Chrome no Android / Safari no iOS).

6. COMO TESTAR
--------------
1. Abre a página Web no telemóvel e concede permissão de acesso à câmara.
2. Aponta a câmara para a imagem correspondente que foi compilada no ficheiro 
   '02_Bolsos.mind'.
3. O modelo 3D do bolso surgirá ancorado diretamente sobre a folha impressa.