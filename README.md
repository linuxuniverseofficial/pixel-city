# PixelCity

Jogo de mundo aberto para navegador, inspirado no GTA 1: personagens em pixel art 2D exploram uma cidade 3D procedural, com veículos, física de pneus, polícia, armas, missões, interiores, rádio, clima dinâmico e segredos.

**Documentação atualizada em 4 de novembro de 2026**, a partir do código atual e das anotações de mecânicas do projeto. O nome atual do jogo e dos novos saves é **PixelCity**. Não foi atribuído um número novo de versão ao jogo.

## Visão geral

- Jogo concentrado em **um único `index.html`**, com HTML, CSS e JavaScript.
- Renderização WebGL com Three.js; sprites, texturas e grande parte dos modelos gerados por código.
- Sem servidor de aplicação, banco de dados ou etapa de build para jogar.
- Dois tamanhos: **Mobile · 7×7** e **Normal · 14×14**.
- Cidade estática gerada por seed e pré-carregada antes da partida.
- Teclado e mouse, controle e interface de toque.
- Progresso exportado manualmente para arquivos `.psave`.

A proposta continua a mesma: ser simples, completo e divertido, preservando o visual low poly e a mistura de personagens 2D com cenário 3D.

## Como rodar

1. Baixe e extraia o pacote completo, mantendo o HTML, os arquivos PWA e a pasta de ícones juntos.
2. Abra no navegador com WebGL ou sirva o arquivo por HTTP/HTTPS em uma hospedagem estática.
3. Escolha o tamanho e a hora inicial.
4. Use **GERAR NOVA CIDADE** para sortear uma seed ou **GERAR COM ESTA SEED** para usar o valor do campo.
5. Aguarde a geração e a preparação das regiões, texturas e materiais.

O arquivo concentra o código do jogo, mas **não é um pacote totalmente offline**: bibliotecas e fontes externas são carregadas pela página. Rádio online também depende de conexão. Para usar músicas próprias, adicione arquivos em **CONFIGURAÇÕES → RÁDIO** ou disponibilize a pasta `radios/` junto ao HTML, com uma subpasta por rádio.

Servir por HTTP/HTTPS é preferível para recursos de áudio, leitura das músicas do servidor e políticas do navegador. Ao abrir via `file://`, alguns desses recursos podem ficar limitados. O navegador pode exigir um clique ou toque para liberar o áudio.

## Atualizações recentes

- Rádios por pasta: cada subpasta de `radios/` é uma rádio e a roda mostra só os nomes das pastas. Pastas `Synthwave` e `Mundo Invertido` viram a trilha do mundo correspondente, que entra sozinha e toca também a pé.
- Aves: gaivotas e pássaros aparecem em qualquer ponto do mapa, com 50% de chance cada. As gaivotas deixaram de ficar presas à praia.
- Aves com as cores certas: antes todas eram desenhadas quase pretas (o buffer de cor por instância nascia vazio). Os pássaros ficaram marrom-claro e as gaivotas, brancas. Um pouco de luz própria evita que a parte de baixo vire silhueta.
- Mar no mesmo nível dos rios: a praia inteira virou uma rampa suave (cerca de 9°) do calçadão até a linha d'água, e o rio deságua no mar sem degrau.
- Foz refeita: o canal é a própria água do mar entrando até debaixo da ponte, com margens de areia que acompanham a rampa da praia. A água inclinada e o mar "avançando" sobre o rio foram eliminados.
- A ponte da foz passou a ser uma ponte comum (laje, pilar e muretas iguais às outras), sem os casos especiais que existiam só para ela. As cabeceiras ganharam muretas que fecham a borda da avenida e do calçadão sobre as margens.
- Farol: corrigidas as duas falhas de malha na junção do caminho com a ponta redonda. As pedras subiram para as bordas do caminho, e nenhum objeto de praia aparece sobre ele.
- Cabeceiras da ponte da foz: removida uma face antiga que ficava no mesmo plano da parede nova e causava serrilhado (z-fighting).
- Cabeceiras da ponte da foz: a borda da rampa de areia ficava na face da mureta e vazava como um risco amarelo em ângulos rasantes. Agora ela começa escondida dentro da mureta.
- Trechos de costa sem areia, fora da cidade ou no lado sem praia, têm cais de pedra até a água. As pontas da praia são fechadas com parede.
- Fundo do mar visível: o asfalto deixou de passar por baixo do mar.
- Guarda-sóis, toalhas, espreguiçadeiras, banhistas e o alvo do paraquedas acompanham a inclinação da areia. A marina ficou baixa, perto da água, e o farol passou a sair do alto da praia como um molhe de pedra.
- Fuga pelo shopping: dá para entrar procurado. As viaturas vão até a porta e os policiais entram atrás do jogador e o seguem pelos andares, mas não atiram lá dentro. Com o provador aberto, ninguém é preso.
- Comprar roupa nova durante a perseguição rebaixa o procurado para busca na área do crime. Se o veículo continuar o mesmo, a perseguição volta depois de 1 minuto dentro da zona; se ele também tiver sido trocado, a busca termina.
- Pintar o carro na oficina conta como troca de veículo, inclusive durante a perseguição. Consertar no posto não conta.
- Descer do carro não conta como trocar de veículo: a pé, a polícia continua associando o jogador ao último carro usado.
- A buzina voltou a controlar a viatura: um toque rápido liga ou desliga sirene e giroflex; segurar toca a buzina. A buzina do jogador dura enquanto o botão estiver pressionado e não acumula mais quando é tocada repetidamente.
- Removido o aviso VEÍCULO ROUBADO.
- Limpeza de código: restos de avisos removidos, variáveis e funções sem uso eliminadas.
- Instalação como PWA no celular e em navegadores de desktop compatíveis, com abertura em tela cheia e orientação paisagem no mobile.
- Novos saves `.psave` criptografados e autenticados; mensagem de erro própria ao importar arquivos inválidos.
- Mundo Invertido com até dez demogorgons, perseguição, saltos e pontos vermelhos no mapa.
- Ônibus com letreiros de destino: CENTRO, PRAIA e INDUSTRIA.
- Chuva regional sem preferência pela posição do jogador; aves desaparecem na chuva e paraquedistas NPC são retirados na chuva forte.
- Viaturas estacionadas na delegacia.
- Suspeitos revidam nas perseguições ambientais; viaturas destruídas podem ser substituídas por reforços.
- Oficina cobra pintura, instalação de nitro e reparos. Casa e troca de roupas já adquiridas continuam gratuitas.
- Dinheiro de pedestre atropelado só pode ser coletado a pé.
- Terraço de salto reservado pela seed, com seta amarela e mini paraquedas no mapa; caminhada no teto e salto pelas quatro bordas.
- Controle do paraquedas com curvas, planeio prolongado e descida acelerada; alvo na praia paga $100 sem cheat.
- Espreguiçadeiras na areia, ocupadas por pedestres pixelados; mesas e cadeiras de bar continuam diante de prédios da orla.
- Toalhas e alvo com prioridade de profundidade revista para reduzir o encobrimento pela areia à distância.
- Recorte de prédios, interiores e pontes para melhorar a visibilidade nas câmeras apropriadas.
- Cheat TELEPORT pelo marcador do mapa; cheats bloqueiam save e pagamentos de táxi, vigilante e alvo do paraquedas.
- Carregamento inicial prepara vistas e recursos gráficos antes de liberar a partida; minimapa mantém atualização de 30 Hz.

## Instalar como aplicativo

O pacote inclui `manifest.webmanifest`, `pwa.js`, `sw.js` e ícones. Não exige PHP nem backend.

- Publique o pacote em **HTTPS**; `localhost` também permite desenvolvimento local com os recursos necessários.
- Em navegadores compatíveis, use **INSTALAR PIXELCITY** ou a opção de instalação no menu do navegador.
- No Safari do iPhone/iPad, use Compartilhar → Adicionar à Tela de Início.
- O aplicativo solicita abertura em tela cheia e orientação paisagem. No mobile, a interface também orienta a girar o aparelho; o bloqueio efetivo depende do navegador.
- Instalar adiciona um atalho/aplicativo web: o jogo continua usando o navegador e WebGL.
- O service worker atual usa rede, sem cache offline do jogo. Instalação não significa funcionamento offline; dependências e rádio continuam precisando de conexão.
- A instalação não substitui o salvamento manual em `.psave`.

## Menu e configurações

### Menu principal

| Opção | Comportamento |
|---|---|
| Mobile · 7×7 | Cidade compacta, com prioridade para os edifícios especiais |
| Normal · 14×14 | Cidade maior, com dois rios e conexão com o mar |
| SEED | Consulta ou edição do número usado para gerar a cidade |
| SORTEAR | Preenche o campo com outra seed |
| GERAR COM ESTA SEED | Gera usando o número informado; botão abaixo do campo |
| GERAR NOVA CIDADE | Sorteia uma seed e inicia outra cidade |
| HORA INICIAL | Define o horário de início |
| CONTINUAR | Retorna à partida; botão verde |
| CARREGAR SAVE | Importa um arquivo `.psave` |
| SALVAR JOGO | Exporta o progresso da partida |
| CONFIGURAÇÕES | Abre os ajustes por categoria |
| COMANDOS | Abre controles, cheats e FAQ |
| MONITOR | Alterna o painel de desempenho; fica vermelho quando ativo, sem acrescentar “ligado” ao texto |

Uma partida nova começa em **Modern**, com câmera de terceira pessoa. Synthwave e Mundo Invertido fazem parte dos segredos do jogo; um save pode restaurar o estilo em que foi salvo.

### Categorias de CONFIGURAÇÕES

- **ÁUDIO:** volume geral, música/rádio, efeitos e som ligado/desligado.
- **RÁDIO:** fonte das músicas, arquivos próprios e teste de reprodução.
- **MUNDO:** densidade de trânsito e pedestres, aplicada durante a partida.
- **GRÁFICOS:** limite de FPS, resolução interna, iluminação dos postes, quantidade de luzes reais, sombras, bloom e reflexos do piso molhado.
- **INTERFACE:** exibição do HUD e do minimapa.
- **CONTROLE:** estado do gamepad, vibração, sensibilidade, zona morta, inversão do eixo Y e teste de vibração.
- **GERAL:** restauração das configurações padrão.

Os ajustes ficam no navegador e também acompanham o save. A lista de códigos está em **COMANDOS → CHEATS**. **RESTAURAR PADRÕES** exige um segundo clique para confirmar.

## Controles

### Teclado e mouse

| Comando | Ação |
|---|---|
| W A S D / setas | Andar ou dirigir |
| Shift | Correr; nitro em veículo equipado |
| F | Entrar, sair ou roubar veículo; interações contextuais |
| Espaço | Pular a pé; freio de mão no carro |
| Clique esquerdo | Atirar; sem arma, socar; segurar dispara rajada quando a arma permite |
| R | Soco a pé |
| TAB segurado | Roda de armas, com tempo desacelerado; soltar confirma |
| TAB rápido | Próxima arma |
| 1 / 2 / 3 / 4 / 5 | Punhos / Pistola / Colt Magnum / Metralhadora / Bazuca |
| Roda do mouse a pé | Trocar arma |
| E | Ação a pé. No veículo, segure para buzinar. Na viatura, um toque rápido liga ou desliga sirene e giroflex |
| H | Faróis |
| Q segurado | Roda do rádio, incluindo DESLIGADO |
| Q rápido | Próxima opção do rádio |
| . / , | Próxima / anterior música |
| Roda do mouse no carro | Trocar música |
| W + S + A ou D | Zerinho |
| Clique esquerdo na bomba | Abastecer, com o veículo parado junto à bomba |
| Botão direito na bomba | Consertar o veículo |
| Mouse | Olhar na visão 3D; clique para capturar o cursor |
| V | Alternar câmeras |
| Z / C ou botão direito arrastando | Girar a câmera em perspectiva |
| + / − | Zoom da perspectiva |
| M ou clique no minimapa | Abrir/fechar o mapa |
| Clique direito no mapa | Marcar/desmarcar destino do GPS |
| T | Iniciar/encerrar missão de táxi ou vigilante |
| N | Som ligado/desligado |
| F3 | Monitor de desempenho |
| ? / F1 | Comandos |
| ESC / P | Menu |
| ' | Caixa de cheat; digite e confirme com Enter |

**Paraquedas:** encontre o mini paraquedas no mapa e a seta amarela na entrada. Use **E/AÇÃO** para subir e, perto de qualquer borda, para saltar. No ar, ←/→ fazem curvas, ↑ prolonga o planeio e ↓ acelera a descida.

### Controle

Conecte por USB/Bluetooth e pressione um botão para o navegador detectá-lo. Layout inspirado no GTA V:

| Botão | Ação |
|---|---|
| Analógico esquerdo | Andar / dirigir |
| Analógico direito | Olhar / escolher nas rodas |
| R2 / RT | Atirar a pé; acelerar no veículo |
| L2 / LT | Freio e ré |
| △ / Y | Entrar / sair |
| ○ / B | Soco; consertar no posto |
| ✕ / A | Segurar para correr; nitro no carro |
| □ / X | Pular; drive-by no carro; abastecer no posto |
| L1 / LB segurado | Roda de armas |
| R1 / RB | Freio de mão |
| L1 + R1 | Drive-by |
| L3 | Segure para buzinar; toque rápido na viatura alterna sirene e giroflex; correr a pé |
| D-pad ← | Rádio no carro; segurar abre a roda; arma anterior a pé |
| D-pad → | Faróis no carro; ação contextual/próxima arma a pé |
| D-pad ↑ / ↓ | Próxima música / missão |
| R3 | Câmera |
| SHARE / VIEW / BACK ou touchpad | Mapa |
| OPTIONS / START | Menu |

R2 + L2 + direção faz zerinho. Nos menus, setas navegam, ✕ confirma, ○ volta e ←/→ ajustam sliders. Vibração depende do navegador e do controle; responde a colisões, tiros, explosões, pousos, terreno, nitro e trovões.

### Celular e tablet

- Joystick à esquerda para movimento e direção; arrastar na área livre controla a câmera.
- Botões de tiro/soco, entrar/sair, pulo/freio, correr/nitro, arma e buzina/ação conforme o contexto.
- Acessos de mapa, câmera e rádio na interface de toque.
- No mapa, toque e segure para marcar um destino.
- Controles de toque ficam ocultos durante menus, oficina e provador.
- Minimapa, barras e nomes abreviados dos locais usam disposição adaptada à tela.
- Jogo orientado para uso em paisagem; na câmera isométrica, o direcional de toque do carro acompanha a direção indicada pelo analógico na tela.

## Cidade procedural e seeds

A geração estática usa a seed: ruas, lotes, edifícios, detalhes e posicionamento dos elementos do mundo devem se repetir com **a mesma seed, tamanho, estilo e versão do jogo**. Trânsito, pedestres, chuva e eventos continuam dinâmicos e aleatórios.

Alterações no gerador podem mudar uma cidade entre versões, mesmo com a mesma seed. O save reconstrói o cenário com o gerador disponível; não contém uma cópia completa de todas as malhas.

### Zoneamento e arquitetura

- Centro denso, bairros urbanos, áreas residenciais, indústria e zona rural, conforme posição do centro e espaço disponível.
- Quarteirões de formatos variados, parques, praças, estacionamentos e becos.
- Edificações procedurais especiais têm área de implantação limitada a **até duas quadras**, evitando hospitais e outros prédios gigantes ocupando três ou quatro. Um distrito industrial pode reunir mais de um lote.
- Prédios com portas e janelas organizadas, marquises, parapeitos, adornos, ar-condicionado, caixas d’água, antenas e iluminação noturna.
- Prédios abandonados com composição de fachada revisada, incluindo portas, janelas e fechamentos.
- Casas com telhados, portas, janelas, caminhos, detalhes de fachada, varais, lixeiras e, em alguns lotes, piscina e churrasqueira.
- Gramados residenciais unidos visualmente, sem as divisórias artificiais entre placas.
- Cerca de **40% das casas** recebem cercas leves: madeira marrom ou modelo branco com tábuas paralelas.
- Árvores com copas mais arredondadas, preservando o estilo low poly.
- Texturas procedurais reutilizadas: grama verde salpicada, calçada rugosa com juntas e linhas de telhas nos telhados.

### Edifícios especiais

**Mobile e Normal reservam espaço para os marcos**, em vez de sortear quais ficam de fora:

| Local | Destaque |
|---|---|
| Arranha-céu | Torre alta, recuos e antena iluminada |
| Prefeitura | Colunas, frontão, escadaria e cúpula |
| Hospital | Cruz vermelha, alas, heliponto e ponto de renascimento |
| Universidade | Campus com gramado e torre do relógio |
| Estádio | Arquibancadas, gramado e refletores |
| Banco | Fachada de pedra, colunas e caixas eletrônicos |
| Supermercado | Galpão comercial e estacionamento |
| Shopping | Interior de dois andares, lojas e escada rolante |
| Cemitério | Túmulos, mausoléu, neblina baixa, coletáveis e fantasma |
| Delegacia | Referência da polícia e prisão |
| Postos | Combustível, reparos e conveniência |

No **Mobile**, os marcos têm prioridade; a indústria usa o espaço restante e a zona rural vem depois. Portanto, a presença e a extensão dessas duas regiões podem ser reduzidas.

### Ruas, indústria e campo

- Avenidas de quatro faixas, ruas de mão dupla e de mão única, faixas de pedestre e esquinas arredondadas.
- Postes, cabos elétricos, semáforos amarelos de três lentes e objetos destrutíveis.
- Indústria com galpões, tanques, tubulações, chaminés, contêineres, muros/alambrados e guaritas. **Cancelas abrem por aproximação**.
- Indústria próxima ao rio pode produzir uma mancha de poluição irregular, com espuma, óleo e tambores; a água limpa fora da mancha mantém seu próprio visual.
- Zona rural com estradas de terra, árvores, pedras, fazendas, cercas e feno. Menor aderência, poeira e ausência de iluminação urbana em vários trechos.
- **Atoleiros:** manchas arredondadas escuras, visíveis e ativas durante a chuva, com gradiente de profundidade e sem pares obrigatórios lado a lado. São geradas por seed em trechos rurais, podendo haver uma ou várias. Reduzem muito a aceleração de carros pequenos, mas permitem sair lentamente. Picapes, caminhões, SUVs e ônibus não sofrem esse atolamento; vans sofrem menos. As manchas foram ampliadas e não exibem aviso de atolamento.

## Rios, pontes e mar

### Rede fluvial

- No tamanho **Normal**, são gerados **dois rios principais**, ligados por um canal.
- Um braço da rede chega à praia e deságua no mar.
- O Mobile usa uma geração mais compacta, sem a garantia de dois rios e de uma foz marítima como no Normal.
- Rios rebaixados aproximadamente **3 metros**, no **mesmo nível do mar**, com paredes de concreto e muretas nas margens.
- Pontes em ruas selecionadas, algumas com arco e tirantes; carros passam sobre a laje e lanchas passam sob ela, desviando dos pilares.
- Mapa e minimapa representam rios, conexões e pontes.

### Foz da praia

A avenida da praia cruza o canal por uma ponte comum, igual às outras da cidade. O rio chega ao mar no mesmo nível, sem rampa de água:

- A água do canal é a própria água do mar, que entra até debaixo da ponte. A emenda com a água do rio fica escondida sob a laje.
- Leito do canal desce suavemente do fundo do rio até o fundo do mar, com a mesma textura.
- Margens de areia em rampa dos dois lados (10 m), acompanhando a inclinação da praia até sumirem na linha d'água. O jogador pode escorregar para dentro da água e se afogar.
- Muretas nas cabeceiras: continuam a mureta da ponte pela borda da avenida e fecham o calçadão sobre a margem.
- Pilar central sob a ponte, com passagens navegáveis pelos dois lados. As lanchas vão do rio ao mar aberto sem obstáculo.
- Espuma da arrebentação interrompida na boca do canal.
- Exclusão de píeres e objetos de praia na área da foz: guarda-sóis, cadeiras e outros elementos não ocupam o canal.
- Pedestres comuns são impedidos de atravessar o leito como se fosse chão.

### Lanchas e píeres

- Píeres nas margens com escada, deck, guarda-corpo e lancha. A marina na praia, fora da foz, começa na areia e fica baixa, perto da água.
- **F** entra na lancha quando o jogador está próximo. Para sair, encoste num píer ou numa praia válida.
- Casco em V, proa, balanço, aceleração, deriva lateral e rastro de espuma.
- Colisão com margens e pilares, mantendo o vão sob o tabuleiro navegável.
- Tráfego fluvial de NPCs: rotas construídas por **células de água adjacentes**, sem calcular atalhos pelo ponto médio de rios unidos.
- Curvas suavizadas, afastamento das margens, margem para pilares, verificação do trecho de movimento e tentativa de recuperação quando a rota fica bloqueada.
- Corpo boiando como evento de exploração, com dinheiro ou arma para recolher de barco.

### Água e litoral

- Mar no mesmo nível dos rios (cerca de 3 m abaixo da rua). Água transparente, fundo com areia, pedras e algas visível, ondas e reflexos animados e cardumes.
- Praia em rampa suave: plana na faixa das barracas, depois desce até a linha d'água e continua submersa até o fundo. A areia escurece perto da água (areia molhada).
- Onde não há areia (fora da cidade ou no lado sem praia), um cais de pedra desce da borda do terreno até a água. As pontas da praia têm parede de fechamento.
- Praia em um dos quatro lados, podendo ocupar todo o lado ou apenas parte dele.
- Calçadão, palmeiras, barracas, guarda-sóis, toalhas, banhistas e fogueiras.
- Mesas e cadeiras de bar diante de alguns prédios, exclusivas da praia, com NPCs sentados.
- Espreguiçadeiras distribuídas **na areia da praia**, com NPCs pixelados deitados e elevados à altura do móvel. Não ficam mais nas portas dos hotéis.
- Ocupantes das cadeiras de bar também usam sprites de pedestres comuns; cada vaga tem ocupação e reposição independentes.
- Toalhas acima da areia, com tratamento próprio de profundidade para reduzir seu desaparecimento à distância.
- Banhistas recolhem-se na chuva e retornam depois.
- Farol com acesso ao topo e iluminação noturna. O caminho de areia curvo sai do alto da praia e segue como um molhe elevado, com saias de areia até a água. Ele se abre suavemente até a ponta redonda, sem cantos, e tem pedras ao longo das duas bordas. Guarda-sóis, espreguiçadeiras, toalhas e fogueiras não aparecem sobre o caminho nem ao lado dele.
- Cair em água profunda a pé afoga; veículos terrestres afundam. Piscinas residenciais têm comportamento próprio e não equivalem ao mar.

## Paraquedas

### Encontrar e acessar o terraço

- A geração reserva um prédio da orla para salto; a escolha é derivada da seed. A mesma seed e versão mantêm a escolha, e outros terraços válidos podem completar até três acessos.
- A entrada tem **seta amarela**, no mesmo estilo da casa segura.
- Um **mini paraquedas ciano e rosa com contorno preto** marca a entrada no mapa e aparece no minimapa quando está próximo. A legenda identifica SALTO DE PARAQUEDAS.
- Use E/AÇÃO a pé, junto da entrada, para subir. É possível caminhar pelo terraço.
- A interação de salto aparece ao chegar perto de **qualquer uma das quatro bordas**.
- Saltar pelo lado da praia dá uma trajetória inicial rumo à areia; pelos outros lados, o impulso segue para fora daquela borda, sem retornar automaticamente para a praia.

### Controlar o voo

| Entrada | Efeito durante o salto |
|---|---|
| ← / A ou analógico para a esquerda | Faz curva para a esquerda |
| → / D ou analógico para a direita | Faz curva para a direita |
| ↑ / W ou analógico para a frente | Inclina levemente, reduz a descida e aumenta o alcance |
| ↓ / S ou analógico para trás | Inclina para baixo e acelera a descida |
| Sem entrada | Mantém direção e planeio normal |

No terraço, o direcional continua servindo para caminhar. No ar, o comando para cima prolonga o planeio, sem permitir subir indefinidamente. O paraquedas tem inclinação suave durante essas manobras.

### Alvo e NPCs

- Ao saltar, surge um círculo vermelho na areia. Pousar a até aproximadamente **3,1 m** do centro rende **$100**, desde que a partida não tenha usado cheat.
- O alvo é opcional: pode-se saltar e explorar outras direções.
- A descida neutra do jogador e a dos NPCs usam cerca de **2 m/s**; os comandos alteram a descida do jogador.
- NPCs escolhem entre até três pontos próximos na areia, evitando a foz. No máximo dois saltadores ficam ativos simultaneamente.
- Chuva forte no voo ou no destino retira o paraquedista NPC; novos saltos também verificam o tempo.
- Pousar na água continua sujeito ao afogamento. Não é permitido salvar enquanto estiver no terraço ou durante o salto.

## Veículos e trânsito

### Modelos e física

Sedã, táxi, viatura, esportivo, conversível, hatch, SUV, van, picape, caminhão, ônibus, superesportivo, moto e lancha têm modelos procedurais próprios.

- Carrocerias por seções arredondadas, vidros inclinados, teto, para-choques, retrovisores e faróis/lanternas.
- Esportivos com inspiração leve nas proporções de carros reais, sem buscar réplicas exatas.
- Física de corpo rígido com pneus, aderência lateral, controle de tração, freio de mão, derrapagem, marcas, fumaça e inclinação da carroceria.
- Piso molhado e terra alteram a aderência; lama rural também afeta a força disponível.
- Nitro em veículos equipados; zerinhos com fumaça e consumo adicional.
- Dano, incêndio, explosão e reações em cadeia.
- Motos inclinam nas curvas e usam piloto em sprite 2D. Impactos fortes podem derrubar o jogador.
- Faróis, som de motor por categoria, buzina e neon inferior em parte dos veículos.
- Buzina e giroflex da viatura ficam no mesmo botão: um toque rápido liga ou desliga sirene e giroflex; segurar toca a buzina. A buzina dura enquanto o botão estiver pressionado e nunca sobrepõe outra.
- Câmera veicular em primeira pessoa posicionada sobre o capô ou à frente do para-brisa, conforme o modelo.

### População do trânsito

- Tipos de veículos variam por região: esportivos/conversíveis na orla, utilitários nos bairros e campo, táxis no centro.
- Trânsito ajustável, com veículos distantes simplificados e física mais detalhada perto do jogador.
- Ônibus exibem destinos CENTRO, PRAIA ou INDUSTRIA nos letreiros.
- Duas viaturas estacionadas são previstas diante da delegacia, separadas da cota de patrulhas ambientais.
- Semáforos, filas, mão única, buzinas e manobras de recuperação.
- Semáforo derrubado ou em alerta pisca amarelo visualmente; a IA continua seguindo o ciclo de tráfego para evitar caos no cruzamento.
- Carcaças e veículos removidos deixam de ocupar permanentemente a cota de população: o sistema pode repor veículos conforme a limpeza ocorre.
- Helicópteros e aviões têm **três fluxos por tipo**, aumentando a frequência em relação ao sistema anterior; intervalos e rotas continuam aleatórios.

### Oficina e garagem

- Oficina marcada em magenta, com pintura por paleta/cor livre, nitro e reparos. A pintura conta como troca de veículo para a polícia; durante a perseguição, rebaixa o procurado para busca na área do crime.
- Garagem da casa segura com duas vagas: guarda veículos compatíveis, conserva cor e nitro e permite repará-los ao estacionar.
- Caminhões e ônibus não cabem nas vagas domésticas.
- Serviços exigem saldo antes da aplicação; sem dinheiro, a alteração não é realizada.

| Serviço | Preço / regra |
|---|---|
| Pintura na oficina | $50 por aplicação de uma cor diferente |
| Nitro na oficina | $250; não cobra de novo se já estiver instalado |
| Reparo na oficina ou no posto | `ceil((100 − vida do veículo) × 1,2)` |
| Recuperação na casa e reparo da garagem doméstica | Gratuitos, nas condições de interação existentes |
| Reequipar roupa/cor já adquirida | Gratuito |

A cor livre é aplicada ao confirmar a mudança, evitando cobranças contínuas enquanto o seletor é arrastado.

## Combustível, postos e conveniência

- Veículos terrestres dirigidos pelo jogador usam combustível; aceleração, nitro e zerinho consomem mais.
- Barra de combustível com alerta de nível baixo. Sem combustível, o veículo perde propulsão.
- Pare junto à bomba: clique esquerdo abastece; direito conserta. No controle, □/X e ○/B.
- Abastecimento custa **$0,60 por ponto percentual**; reparo depende do dano e do dinheiro disponível.
- Postos com cobertura, bombas, preços, loja e identidade visual própria; no Synthwave, paleta pastel e neon ciano/rosa.
- Bombas podem explodir por tiros, impactos fortes ou explosões próximas, causando reação em cadeia.
- Posto destruído fica chamuscado, temporariamente indisponível e reabre depois de um dia do jogo.
- Loja de conveniência com interior, caixa e produtos. Lanche de **$15 recupera 50 de vida**.
- Ameaçar o caixa com arma inicia assalto; violência aciona alarme e reação policial. Não é permitido entrar estando procurado.

## Personagem, armas e dinheiro

- Personagens em sprites procedurais de **32×48 pixels**, com animação direcional, roupas, rosto e acessórios.
- Pedestres caminham, conversam, olham vitrines, entram/saem de edifícios, fogem e reagem à chuva e à violência.
- Pulos sobre obstáculos baixos e possibilidade de subir em carros baixos.
- Punhos, pistola, Colt Magnum, metralhadora e bazuca; seleção direta ou por roda.
- Pistola/metralhadora exigem vários acertos no corpo; tiros na cabeça são letais. Magnum causa dano alto e tem cadência menor; bazuca causa explosão em área.
- Drive-by, danos em veículos e reação policial aos disparos.
- Armas, munição e kits de vida encontrados nos becos e no cemitério.
- Pedestres atropelados podem deixar **$0 a $50**. Quando o valor é zero, nada aparece; o dinheiro deixado fica disponível por tempo limitado.
- Esse dinheiro de atropelamento só é recolhido **a pé**, sem entrar no raio de coleta com carro, moto ou lancha. O evento de corpo boiando mantém sua coleta específica de barco.
- Coletável de dinheiro em formato de cifrão 3D, com tamanho reduzido.
- Dinheiro usado em combustível, reparos, comida e roupas, além de ser recebido por missões e coletáveis.

## Polícia e missões

### Procurado

A polícia reage a crimes presenciados, ataques a viaturas/policiais e violência contra pedestres. Viaturas patrulham, calculam rotas, perseguem, tentam se desatolar e podem trazer reforços; policiais também saem e atiram a pé.

A fuga acontece por afastamento da área do crime ou por disfarce (roupa nova ou pintura do carro). Destruir viaturas ou abater policiais não encerra a perseguição. Ser encurralado e imobilizado pode resultar em prisão. Morte leva ao hospital; prisão usa a delegacia.

### Reconhecimento por região

- Após escapar, permanece uma **zona vermelha** no mapa.
- A polícia registra roupa e veículos vistos durante a perseguição.
- Voltar com roupa e veículo reconhecidos pode reiniciar a perseguição; correspondência parcial permite um breve período de suspeita.
- Roupa e veículo são os dois indicadores. Com os dois reconhecidos, a perseguição recomeça na hora; com apenas um, depois de 1 minuto dentro da zona; sem nenhum, a busca termina.
- O veículo considerado é o atual ou, a pé, o último usado. Descer do carro não é trocar de carro.
- Pintar o carro na oficina muda o veículo reconhecido. Consertar no posto não muda.
- Comprar roupa no shopping ou pintar o carro **durante a perseguição** rebaixa o procurado para busca na área do crime, e as regras acima passam a valer.
- Ficar longe da zona por uma hora do jogo faz a memória local expirar.
- Indicadores de roupa/carro mostram o estado de reconhecimento; as zonas são incluídas no save.

### Missões de veículo

- **Táxi — T:** buscar passageiro, parar para embarque e seguir o GPS até o destino. Pagamento por distância e possível gorjeta; dano excessivo pode fazer o passageiro desistir.
- **Vigilante — T na viatura:** enfrentar cinco níveis de suspeitos em fuga, de uma moto até grupos de carros, com tempo limitado. O nível final paga $500. Não começa enquanto o jogador está procurado.
- T novamente encerra a missão. Perseguições ambientais também podem ocorrer sem envolver o jogador.
- Nessas perseguições ambientais, suspeitos revidam contra as viaturas; perdas podem chamar reforços, até três viaturas desejadas no evento.
- Usar cheat bloqueia os pagamentos de táxi e vigilante durante a sessão.

### Rampas e saltos insanos

Rampas em estacionamentos e becos permitem saltos. No ar não há tração; pousos fortes danificam o veículo e podem derrubar o motociclista. Saltos insanos usam câmera cinematográfica e recompensa na primeira conclusão; o progresso fica no save.

## Casa segura, roupas e shopping

### Casa segura

- Marcada por casa amarela no mapa e seta na entrada.
- Interior com móveis, cozinha, cama, TV, guarda-roupa e objetos decorativos.
- Entrada recupera vida e pode reparar o veículo próximo; **não salva automaticamente**.
- Guarda-roupa permite trocar gratuitamente entre **cores e acessórios já adquiridos**; itens não comprados ficam bloqueados.
- TV acessada por F apresenta transmissão de tempestade ou perseguição; esquerda/direita mudam o canal e F encerra.
- O canal de tempestade começa com céu fechado e chuva forte. Ao sair, o clima exterior é restaurado e o molhado artificial da transmissão é removido, sem deixar poças da TV no mundo.

### Shopping e MODA PIXEL

- Shopping de dois andares, átrio, fonte, palmeiras, bancos, vitrines, galeria e escada rolante.
- Lojas de moda, conveniência, games, tecnologia, livros, café, ótica, joias, sapatos, brinquedos, música, esportes, perfumes, pizza, farmácia e cinema.
- Interior com paleta revista nos dois estilos e **bloom reduzido**, mantendo a atmosfera pastel/vaporwave sem ofuscar o cenário.
- MODA PIXEL oferece provador com prévia frontal/lateral: camisa, calça, calçado, boné, óculos e colar.
- Cada nova cor/acessório custa **$10**; opções já compradas podem ser reequipadas gratuitamente.
- Compras e visual atual ficam no save e alimentam o guarda-roupa doméstico.
- Balões contextuais indicam as ações nas lojas; a conveniência vende comida.
- É permitido entrar no shopping procurado. As viaturas param na porta, e os policiais entram, seguem o jogador entre os andares e tentam prendê-lo sem atirar. Com o provador aberto, não há prisão. Comprar roupa nova rebaixa o procurado para busca na área do crime.

## Dia, noite e clima

### Relógio, céu, sol e lua

- **1 segundo de simulação equivale a 1 minuto do jogo**: um dia completo dura aproximadamente 24 minutos sem pausas.
- Sol com trajetória leste–oeste, iluminação e sombras variando ao longo do dia.
- Modern com amanhecer e pôr do sol dourado, pêssego, laranja e violeta; Synthwave mantém sua paleta retrô.
- Nuvens leves de fundo separadas das células de chuva, com cobertura variável.
- Lua em quatro fases: nova, crescente, cheia e minguante; fase inicial relacionada à seed e avanço com as noites.
- Crescente/minguante usam sombra curva, em vez de corte reto.
- **Lua nova não produz reflexo no mar**; crescente e minguante usam metade da força do reflexo da cheia.
- Estrelas, janelas, postes e faróis compõem a iluminação noturna.

### Chuva natural

- O clima da seed influencia a probabilidade de chuva, mas o momento de cada evento é aleatório.
- Células se formam, movem-se com o vento e se dissipam; a chuva é regional.
- A distribuição não favorece a posição do jogador: pode começar longe, já existir em outras áreas no início ou não começar naquele momento. Não usa pontos fixos nos cantos/centro do mapa.
- Previsões avisam a formação e a direção. Mapas mostram áreas de chuva e setas de movimento.
- Chuva comum não produz raios/trovões: esses efeitos ficam para a tempestade.
- Gotas recebem influência das luzes próximas, piso molha e seca gradualmente, aderência diminui e pedestres buscam abrigo ou usam guarda-chuva.

### Tempestade

- Evento natural com chance de ocorrência; não é mais uma opção manual fixa nem “toda sexta chuva”.
- Antes da chegada, o tempo limpa e a formação de nuvens comuns é suspensa. Essa preparação ganhou tempo extra para evitar a frente surgir com o céu ainda cheio de nuvens antigas.
- A frente aparece no horizonte e atravessa o céu.
- O sol começa a esmaecer com aproximadamente **50% de cobertura**, para que o ambiente esteja escuro quando a frente fechar o outro lado.
- Chuva forte, raios ramificados, clarões e trovão com atraso conforme a distância.
- Árvores, palmeiras, semáforos e varais respondem à mesma direção de vento. A orientação do objeto e a intensidade alteram a amplitude visual.
- Caixas dos semáforos balançam como pêndulos; luzes piscam amarelo sem desligar a lógica de prioridade do trânsito.
- Folhas voam na ventania; em tempo normal, algumas caem ocasionalmente.
- Folhas com formato e cores de folha, incluindo verde e amarelo-amarronzado, acompanhando a iluminação ambiente para não parecerem iluminadas pelo sol durante a tempestade.
- **Não há tapetes de folhas estáticas no pé das árvores**, removidos para evitar custo adicional.
- O aviso “tempestade · céu totalmente fechado” foi removido.
- Ao terminar, a frente se dissipa e o clima natural retorna.

### Piso molhado e poças

- Molhado acumulado por região e secagem gradual depois da chuva.
- Poças de água e anéis de gotas próximos da câmera; as manchas de lama rural seguem regras próprias de chuva e atolamento.
- **Reflexos simulados**, com cores do céu e rastros de luz: não há uma segunda renderização completa da cidade como no espelho das versões antigas.
- Calçadas usam tratamento mais simples; efeitos distantes são reduzidos.
- Opção para desligar em CONFIGURAÇÕES → GRÁFICOS.

## Segredos e mundos alternativos

### BACK TO THE PAST / Top Secret

Nas garagens especiais há um carro cinza inspirado no DeLorean, associado à viagem entre **Modern e Synthwave**.

- Carroceria e detalhes revisados: placa sobre o capô e barras laterais flutuantes removidas; barrinhas traseiras ajustadas ao vidro.
- Contornos de energia **ciano e rosa nos dois lados**, próximos à carroceria.
- **40 km/h:** contornos começam a acender.
- **70 km/h:** aparece o efeito luminoso à frente.
- **88 km/h:** dispara a viagem quando o sistema está preparado, com transição e recriação do mundo no outro estilo.
- Após a chegada, os efeitos da viagem anterior são desligados; existe intervalo de recuperação antes de outra viagem.

### Fenda e Mundo Invertido

- Fenda posicionada junto à parede de um beco, com vermelho vivo e borda escura que desaparece em transparência.
- Cada aparição dura **60 segundos de simulação**, equivalentes a uma hora do jogo.
- Diminui lentamente; aos 59 segundos está bem pequena, ainda atravessável. Aos 60, deixa de aceitar travessia e desaparece em um breve fade-out.
- Depois muda de beco. Menus que pausam a simulação também pausam esse relógio.
- A travessia leva ao **Mundo Invertido**: cidade escura e dessaturada, horário às 03:00 e atmosfera própria.
- Até **dez demogorgons** perseguem pelas ruas, com movimento aos saltos, aparência pixelada marrom e detalhes vermelhos brilhantes.
- Procuram caminhos, detectam o jogador com verificação de linha de visão e podem causar **25 de dano por ataque**, com intervalo entre ataques. Pontos vermelhos no mapa indicam os monstros.
- Retornar vivo pela fenda concede **$1.000**, conforme as regras do evento.
- A fenda também permite retornar; o mapa fornece referência de sua localização.
- `UPSIDEDOWN` leva para perto da fenda, sem atravessar automaticamente e sem reiniciar sua duração.

### Cemitério

Fantasma translúcido pode aparecer entre os túmulos, perseguir e ferir o jogador. Se matar o jogador, há uma transformação visual em pessoa viva. O cemitério mantém neblina baixa, mas não tem mais uma nuvem escura permanente própria.

## HUD, mapa e câmeras

- Dinheiro exibido no **mapa**, retirado da HUD normal.
- Bússola dentro do mapa, no canto superior direito, liberando espaço para o relógio; vida, arma, procurado e avisos em disposição compacta.
- Barras **VEÍCULO** e **COMBUSTÍVEL** lado a lado, ocultas quando o jogador está a pé.
- Minimapa atualiza a **30 Hz**, preservando custo menor que redesenhá-lo em todo quadro, e gira com a direção do jogador; bússola indica o norte. Mapa grande mantém norte para cima.
- GPS traça rota pelas ruas até o destino marcado e mostra referência no mundo.
- Mapa inclui locais especiais, rios, pontes, chuva, poluição, zonas de reconhecimento e outros pontos de interesse.
- Abrir o mapa grande não pausa a simulação.
- Avisos empilhados com duração própria; nome da música desaparece após alguns segundos.
- Interface com fonte legível; placas e letreiros do cenário preservam a estética pixelada.
- Na isométrica, prédios entre câmera e jogador recebem transparência pontual. Interiores, coberturas de garagem e oficina usam recorte para manter o personagem visível.
- Pontes podem receber recorte pontual quando encobrem o jogador na lancha, nas câmeras isométrica e de cima.
- Seis posições/modos na sequência de V: terceira pessoa, terceira perto, terceira bem perto, primeira pessoa, perspectiva giratória e vista de cima.

## Rádio e áudio

- Configuração em **CONFIGURAÇÕES → RÁDIO**, fora do menu principal.
- Fontes: músicas do servidor + próprias; somente próprias; rádio online KRFM.
- Formatos reconhecidos incluem MP3, OGG, M4A, WAV, OPUS e FLAC, conforme suporte do navegador.
- **Cada pasta dentro de `radios/` é uma rádio.** O nome da pasta é o nome da rádio e os áudios dentro dela são a programação. Arquivos soltos direto em `radios/` formam a rádio **RÁDIO**. A raiz do jogo não é mais lida.
- Exemplo:
  - `radios/Rock FM/*.mp3` → rádio **ROCK FM**
  - `radios/Pagode 90/*.mp3` → rádio **PAGODE 90**
  - `radios/Synthwave/*.mp3` → trilha do mundo Synthwave
  - `radios/Mundo Invertido/*.mp3` → trilha do Mundo Invertido
- **Trilhas de mundo (OST):** pastas chamadas `Synthwave`, `Mundo Invertido` (ou `Invertido`) e `Moderno`. Elas aparecem na roda só dentro do mundo correspondente e são sintonizadas sozinhas ao entrar nele. Também tocam a pé, a 60% do volume. Ao sair do mundo, o rádio volta para a rádio que tocava antes.
- A roda do rádio mostra apenas o nome de cada rádio: 1 pasta, 1 rádio; 2 pastas, 2 rádios. Q rápido troca de rádio.
- Dentro de cada rádio, a ordem das músicas é embaralhada pela seed. Ao terminar uma faixa, toca a próxima da mesma rádio; arquivo com erro é pulado. **Trocar de carro mantém a música em andamento.**
- Requer listagem de diretório no servidor (nginx `autoindex` / Apache `Indexes`). Sem listagem, use `radios/lista.txt` com uma linha por arquivo no formato `Pasta/arquivo.mp3`.
- Músicas adicionadas do computador formam a rádio **MINHAS MÚSICAS**.
- Carros que passam tocam músicas das rádios comuns, nunca das trilhas de mundo. A rádio ao vivo não oferece seleção de rádios locais.
- Equalização, compressão e som espacial quando disponíveis; alguns carros passam tocando música.
- Motor, buzina, pneus, sirenes, tiros, explosões, vento, chuva e trovões usam áudio do jogo.
- Arquivos de música escolhidos no computador não são incorporados ao `.psave`.

## Salvar e carregar

**O jogo não salva automaticamente o progresso no navegador.** Use MENU → SALVAR JOGO e guarde o arquivo `.psave`.

**Formato atual:** `.psave` com envelope JSON e conteúdo criptografado/autenticado em **AES-256-GCM**, com IV aleatório. Exportação usa nomes `pixel-city_seed<seed>_<data>-<hora>.psave`. Requer Web Crypto: use HTTPS ou localhost. A chave está no cliente; esse formato evita edição casual e detecta adulteração, mas não equivale a um sistema antitrapaça de servidor.

O save registra:

- Seed, tamanho, estilo, dia e hora.
- Posição, vida e dinheiro.
- Armas, munição, itens coletados e saltos concluídos.
- Veículo terrestre atual: tipo, cor, dano, nitro e combustível; veículos da garagem.
- Visual do personagem e inventário de cores/acessórios adquiridos.
- Zonas de reconhecimento policial.
- Configurações de áudio, gráficos, mundo, interface e controle.
- Estado de chuva/tempestade, vento, células e piso molhado.
- Estado relacionado à fenda e ao Mundo Invertido.

**Limites e compatibilidade:**

- Não permite exportar enquanto morto, procurado, em missão, no terraço/salto de paraquedas, dentro da prisão ou depois de usar cheat na partida.
- Entrar em casa recupera o personagem, mas não substitui o salvamento manual.
- O importador atual exige o envelope criptografado PixelCitySave v2; arquivos antigos sem criptografia são recusados. Erros de formato ou autenticação abrem uma mensagem própria.
- Saves de tamanhos removidos, como 24×24 e 34×34, são recusados; somente Mobile e Normal são aceitos.
- O arquivo não congela cada NPC/veículo do trânsito nem contém todas as malhas. Carregar recompõe a cidade e restaura os dados suportados.
- Como o gerador evoluiu, uma seed salva em versão antiga pode produzir alterações no cenário da versão atual.

## Cheats

Digite o código durante a partida, use a caixa aberta por **'**, ou consulte as sequências de controle em **COMANDOS → CHEATS**. A caixa evita que as primeiras letras acionem comandos normais. Qualquer cheat marca a partida e bloqueia a exportação de save e pagamentos de táxi/vigilante, além do prêmio do alvo do paraquedas, até iniciar um jogo novo. Desligar um cheat não limpa essa marca.

| Código | Efeito |
|---|---|
| HESOYAM | Vida cheia, $250.000, conserto e tanque cheio do veículo atual |
| AEZAKMI | Alterna nunca ser procurado |
| BAGUVIX | Alterna vida infinita |
| FULLCLIP | Alterna munição infinita |
| LXGIWYL | Pistola e metralhadora |
| KJKSZPJ | Conjunto de armas com Colt Magnum |
| UZUMYMW | Conjunto de armas com bazuca |
| TURNUPTHEHEAT | Inicia perseguição policial |
| TURNDOWNTHEHEAT / ASNAEB | Limpa procurado e zonas vermelhas |
| CPKTNWT | Incendeia/explode veículos próximos, preservando o veículo atual e barcos |
| AUIFRVQS | Inicia a preparação de uma tempestade: limpa o céu antes da chegada |
| AFZLLQLL | Limpa chuva e tempestade e adia novas ocorrências |
| SPEEDFREAK | Instala nitro no veículo atual |
| BACKTOTHEFUTURE | Teleporta para perto do Top Secret na garagem BACK TO THE PAST |
| UPSIDEDOWN | Teleporta para perto da fenda dimensional, sem atravessar |
| TELEPORT | Alterna teleporte ao marcar um destino no mapa; útil para depuração |


### Sequências no controle

Os símbolos abaixo seguem a nomenclatura PlayStation; os botões equivalentes funcionam nos demais controles compatíveis.

| Código | Efeito | Controle (PS2) |
|---|---|---|
| HESOYAM | Vida cheia, +$250.000, conserta e enche o tanque do carro | R1 R2 L1 ✕ ← ↓ → ↑ ← ↓ → ↑ |
| AEZAKMI | Nunca ser procurado (liga/desliga) | ○ → ○ → ← □ △ ↑ |
| BAGUVIX | Vida infinita (liga/desliga) | ↓ ✕ → ← → R1 → ↓ ↑ △ |
| FULLCLIP | Munição infinita (liga/desliga) | L1 R1 □ R1 ← R2 R1 ← □ ↓ L1 L1 |
| LXGIWYL | Armas 1: pistola e metralhadora | R1 R2 L1 R2 ← ↓ → ↑ ← ↓ → ↑ |
| KJKSZPJ | Armas 2: + Colt Magnum | R1 R2 L1 R2 ← ↓ → ↑ ← ↓ ↓ ← |
| UZUMYMW | Armas 3: + bazuca | R1 R2 L1 R2 ← ↓ → ↑ ← ↓ ↓ ↓ |
| TURNUPTHEHEAT | Polícia na cola | R1 R1 ○ R2 ← → ← → ← → |
| TURNDOWNTHEHEAT / ASNAEB | Limpa o procurado e as zonas vermelhas | R1 R1 ○ R2 ↑ ↓ ↑ ↓ ↑ ↓ |
| CPKTNWT | Explode todos os carros por perto | R2 L2 R1 L1 L2 R2 □ △ ○ △ L2 L1 |
| AUIFRVQS | Prepara uma tempestade | R2 ✕ L1 L1 L2 L2 L2 ○ |
| AFZLLQLL | Sol (limpa chuva e tempestade) | R2 ✕ L1 L1 L2 L2 L2 ↓ |
| SPEEDFREAK | Nitro no carro atual | — |
| BACKTOTHEFUTURE | Ir ao Top Secret mais próximo | L1 L2 ↑ ↓ ← → ↑ ↓ |
| UPSIDEDOWN | Ir para perto da fenda | L2 L1 ↓ ↑ → ← ↓ ↑ |
| TELEPORT | Teleporte pelo marcador (liga/desliga) | L1 R1 ← → ↑ ↓ ✕ |

## Desempenho e memória

### Estratégia atual

- Cidade estática **pré-carregada e mantida em memória**; regiões não são descartadas e reconstruídas repetidamente conforme o jogador dirige.
- Preparação antecipada de texturas, shaders, materiais próximos/distantes e regiões na GPU.
- Depois de aplicar o save, o carregamento aquece vistas iniciais em várias direções para reduzir compilação/envios tardios ao girar a câmera; não é apenas uma espera fixa artificial.
- Maior trabalho e uso de memória no carregamento inicial em troca de menos engasgos por reconstrução durante a exploração.
- Regiões fora da visão podem deixar de ser desenhadas sem serem apagadas da memória.
- Objetos temporários, partículas, veículos dinâmicos e recursos de uma cidade substituída ainda são limpos quando necessário. O jogo não desliga o coletor de lixo do navegador.

### Otimizações aplicadas

- Luzes inativas tratadas para evitar trabalho desnecessário; limite de luzes reais de postes, com opção de desligar.
- Resolução do compositor/pós-processamento acompanhando a resolução interna.
- Céu simplificado e texturas procedurais compartilhadas.
- Materiais distantes mais simples e redução/ocultação de pequenos detalhes.
- Instancing para trânsito e menor transferência de buffers quando não precisam mudar.
- Atualização de NPCs e colisões por proximidade/frequência, em vez de calcular tudo com o mesmo custo a cada quadro.
- Chuva e sombras ajustadas; poças com reflexo simulado, sem renderização espelhada completa.
- Folhas voadoras instanciadas, limitadas a 80 no Mobile e 160 no desktop, sem acúmulo de folhas estáticas no chão.
- Modelos e texturas reutilizados, limpeza de entidades removidas e correção de acúmulo de pilotos de moto.

### Ajustes disponíveis

- **Resolução interna:** slider com referência visual PSOne perto de 40%; 0% usa um mínimo seguro, não uma tela de zero pixels.
- **Limite de FPS:** sem limite, 60, 45 ou 30. Limitar FPS controla o teto; não garante que o aparelho alcance esse valor.
- Iluminação dos postes e quantidade de luzes reais, sombras, bloom e reflexos.
- Quantidade de carros e pedestres.
- Mobile usa mapa compacto e configurações iniciais mais econômicas, incluindo iluminação real dos postes desligada.

### Monitor — F3

Mostra FPS, tempo de quadro, tempo de CPU da aplicação, tempo de GPU quando disponível, memória JavaScript quando exposta, estimativa de VRAM, chamadas de desenho, triângulos, geometrias e texturas.

**GPU N/D não significa ausência de placa gráfica.** Significa que o navegador/dispositivo não disponibilizou a medição de tempo de GPU usada pelo monitor. CPU, RAM e VRAM exibidos não equivalem ao uso total do sistema operacional.

O desempenho depende de aparelho, resolução, navegador e cena. A documentação não promete um FPS fixo em celulares ou GPUs integradas. Verificações de sintaxe e testes pontuais de lógica não substituem testes visuais ou medições de FPS no dispositivo. As últimas revisões de sprites de praia, alvo e controle de paraquedas ainda precisam dessa conferência no jogo.

## Tecnologia e organização

- **Three.js r128**, WebGL e pós-processamento.
- Canvas 2D para sprites, mapas, letreiros e texturas.
- Web Audio API e áudio HTML para efeitos e rádio.
- Gamepad API e controles de toque.
- Geração procedural por PRNGs derivados da seed.
- Malhas combinadas, geometria compartilhada, instancing e simplificação por distância.
- Web Crypto API para exportação/importação do conteúdo criptografado em `.psave`; configurações locais no navegador.
- Manifesto web, service worker e interface de instalação PWA.

Estrutura básica para distribuir:

- `index.html`: jogo.
- `README.md`: esta documentação.
- `manifest.webmanifest`: identidade, tela cheia, orientação e ícones da PWA.
- `pwa.js`: interface de instalação e registro do service worker.
- `sw.js`: service worker com estratégia de rede.
- `icons/`: ícones de 180, 192 e 512 pixels.
- `radios/`: opcional; uma subpasta por rádio (e/ou `lista.txt`).

Não são necessários banco de dados, backend ou compilação. O carregamento das dependências externas continua exigindo acesso às respectivas fontes, salvo se a distribuição for adaptada para hospedá-las localmente.

## Fauna e atividade na praia

- Gaivotas brancas (circulando) e pássaros marrom-claro (seguindo as ruas), sorteados meio a meio em qualquer ponto do mapa, com modelos leves e voo em bandos.
- Bandos são retirados de áreas chuvosas; tempestades suspendem a atividade das aves.
- Banhistas deitam durante o dia; fogueiras e atividades noturnas substituem esse uso à noite.
- Mesas de bar ficam diante de alguns prédios da orla; espreguiçadeiras ficam na areia.
- A quantidade de ocupantes é limitada e depende de distância, horário e chuva, para preservar o desempenho.

## Inspirações e desenvolvimento

- [24/7 CLT — Uniday Studio](https://uniday.studio/games/247-clt-early-access?cur=brl&lang=pt-BR)
- [Protótipo de veículos de Pat Kerr](https://patkerr.co.uk/2d-vehicles/)
- GTA 1 como referência de estrutura urbana e exploração; referências visuais e de comandos de outros jogos da série.
- Synthwave/vaporwave e referências cinematográficas nos segredos e veículos especiais.

Projeto desenvolvido por iteração e vibe coding: base criada com auxílio do Claude, seguida de ajustes e expansão com auxílio do ChatGPT/Codex. O README anterior também registrava a contribuição de José no comando de giroflex da viatura, preservada aqui.
