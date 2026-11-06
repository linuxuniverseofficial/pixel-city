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

- **v111:** no helicóptero o minimapa gira com a frente do helicóptero e acompanha a posição dele.
- **v110 – aeroporto suave:** o avião segue uma trajetória contínua (velocidade, subida, rolagem e arfagem filtradas, curvas de raio limitado): sai do hangar, taxia em curva até a cabeceira, espera 10 s alinhado, acelera, rotaciona e decola, faz um semi-C (curva de 180° inclinado) e segue reto até a borda do mapa. A chegada vem pela perna paralela à pista, faz o semi-C até alinhar na final, desce na rampa, arredonda, toca, freia, faz o retorno, taxia pela pista paralela e entra no hangar.
- **v109:** cruz lateral da ambulância centralizada no painel traseiro (não cruza mais a junta da porta corrediça).
- **v108:** NPCs da caçamba aparecem da cintura pra cima (pernas escondidas pela caçamba).
- **v107:** setas piscando também na frente (antes só atrás); frisos laterais, vincos de porta, soleira e faixa do táxi agora são fitas contínuas coladas na curva da lataria (não mais pedaços retos “tortos”); ambulância refeita: faixa fina de ponta a ponta, cruzes laterais coladas, cruz no teto e giroflex sobre o teto reto; marcas de pneu não somem mais na grama das praças/quintais; posto explodido reabre após 6 horas de jogo (6 min) quando você está longe; picapes com 2 NPCs em pé na caçamba apoiados no santantônio (comum na zona rural).
- **v106:** caixas de roda sem cortar a curva do para-lama em nenhum carro (o ombro da lataria fica mais reto sobre as rodas) e com ~5 cm de curso pra roda subir; batente de suspensão: se uma roda chegaria ao topo do arco, a carroceria é empurrada pra cima (a roda nunca entra na lataria — testado subindo e descendo calçada com todos os carros); esportivo com pneu um pouco menor e para-lamas mais cheios; palhetas do para-brisa finas e proporcionais; concessionária só com veículos de terra (+ Vortex) e o carro do giratório não congela mais.
- **v105:** novos modelos arredondados (mesma técnica dos carros: seções + loft + normais suavizadas) — helicóptero (fuselagem em gota com bolha de vidro, cone de cauda, deriva e estabilizador com perfil, carenagem do motor, rotor de 4 pás com ponta pintada, esquis com ponta curva), avião (fuselagem tubular, asas enflechadas com diedro e winglets, motores em naceles com pilone, cauda convencional, janelas, portas e trem de pouso), lancha (casco em V com quina, proa alta, faixa e friso de borda, console com para-brisa envolvente, bancos, volante, motor de popa) e Vortex (saia inflada em gomos, cabine em bolha, duto do ventilador com grade e lemes); subida na calçada mais suave (a roda rola sobre a quina); câmera TPS corrigida dentro da casa de penhores, banco, cassino, assalto e império; logo do jogo ao lado do título no menu.
- **v104:** suspensão por roda — cada roda sente a calçada (20 cm) e a carroceria amortece com mola (sobe, inclina e balança), uma roda de cada vez; viatura que vê seu crime e parte pra cima liga giroflex + sirene (inclusive as estacionadas na delegacia); som de helicópteros e aviões pausa no ESC; carros detalhados a partir de ~1 quarteirão (até 14 carros, 7 no celular) sem custo extra graças ao cache de malhas; racks de teto (crossover, perua, SUV) acompanham a curva do teto, santantônio da picape apoiado nas laterais da caçamba e faixa do táxi colada na lataria; no Império, o aviso “destrua o carro da gangue” só aparece quando você está perto do carro.
- **v103 – meio-termo nas caixas de roda:** o arco agora sempre fica um pouco acima do topo do pneu (o pneu não escapa mais do para-lama), sem invadir a curva do capô; folga de ~5 cm. Esportivo e superesportivo ganharam para-lamas levemente mais altos sobre as rodas (o super também tem rodas um pouco menores); a viatura trocou o alargador preto por friso na cor da pintura; dobra do arco em tom mais suave.
- **v102 – acabamento das caixas de roda:** recorte mais justo (folga de ~3,5 cm em volta do pneu, como em carro de rua), o arco nunca sobe até a curva do capô/para-lama (topo achatado quando a roda é grande pra carroceria), dobra da lataria pra dentro do arco antes do forro preto e friso fino rente à pintura. SUV, crossover, picape, viatura e caminhão mantêm o alargador de plástico preto.
- **v101 – carros mais detalhados:** caixas de roda de verdade (a lateral é recortada e tem forro escuro, então a roda aparece inteira dentro do arco, inclusive esterçada, sem atravessar a lataria; o antigo truque de esconder a metade de cima da roda foi removido), rodas de liga com 5 raios, friso nos arcos (plástico preto em SUV/picape/viatura), vincos de porta, soleira, grade com frisos, placas Mercosul, escapamento (duplo nos esportivos), palhetas, setas âmbar, luz de ré, faróis de neblina e antena. Por tipo: estepe no SUV, santantônio e frisos na caçamba da picape, porta corrediça e portas traseiras com vidro na van, porta de vidro, colunas e grade do motor no ônibus, chaminés, tanque, para-barros e luzes laterais no caminhão, quebra-mato na viatura, aerofólio no hatch, rack no crossover e guarda-corpo no barco. Os detalhes só existem na malha de perto, então não pesam no tráfego distante.
- **v100 – som dos motores:** cada tipo de veículo tem seu próprio ronco (timbre, faixa de rotação, número de marchas e volume). Populares, compactos, esportivos, superesportivos, SUVs/picapes/vans, caminhão/ônibus, moto, barco, jet ski e Vortex soam diferentes; barcos e jet ski não trocam marcha e oscilam com as ondas; o Vortex tem zumbido de turbina. Cada carro ainda tem variação própria de ±6%, e turbo/nitro deixam o som mais agudo e brilhante.
- **v99:** ilhas naturais formadas pelo rio voltaram (agora são feature): além da micro-ilha do pedágio, o rio pode cercar quarteirões, ligados por pontes.
- **Império (v98, estilo Vice City Stories):** arranha-céu, supermercado, universidade, estádio, indústria e aeroporto viram negócios de gangue (ícone de prédio laranja; verde quando é seu; vermelho = indisponível no modo história). Tomada: destrua o carro da gangue na frente → derrube 4 membros armados de pistola → entre (seta) e derrube os capangas de punho/taco e destrua os 3 bens do negócio (tiros ou E) → compre o prédio na porta ($2.500 a $6.000). Depois escolha o ramo: DROGAS (aporte $1.500, $400/dia, risco alto, atacantes de metralhadora), CONTRABANDO ($1.000, $250/dia, risco médio, pistolas) ou ROUBO ($500, $150/dia, risco baixo, tacos). O lucro cai num cofre (até 3 dias) que você recolhe na porta; em ataque o ícone pisca e o lucro para até você derrubar os rivais. Mortes de membros de gangue não contam para a regra dos 10 assassinatos. Progresso salvo no save.
- **Shopping: 4 lojas novas com interior (v97):** CAFÉ (térreo; café $5 = +15 vida; clientes tomando café), JOIAS (térreo; colares e cor da fivela do cinto, $25 cada; o colar saiu da Moda Pixel), MÚSICA · DISCOS (1º andar; clientes de fone; perto das prateleiras você ganha um fone de cortesia e as rádios tocam enquanto estiver na loja) e FARMÁCIA (1º andar; remédio $60 = +100 vida).
- **Banco: interior e assalto (v96):** porta com seta amarela na calçada da frente do banco. Dentro: saguão de mármore, colunas, balcão com vidro e 3 caixas, cofre redondo. No balcão, com arma, E anuncia o assalto: 3 estrelas na hora e 8 policiais entram em ondas atirando; derrubando todos, o cofre abre e paga $1.000. Saída conta como fuga normal (área do crime = porta do banco). Sair antes = assalto fracassado. Banco fecha 1 dia de jogo depois. No modo história o assalto fica trancado (base para a futura missão).
- **Cassino Pixel Royale (v95):** fachada neon com marquise e letreiro num quarteirão perto do centro (ícone de ficha no mapa). Dentro: salão com carpete, 5 caça-níqueis, bar e mesa. No caça-níquel (E/A): $10 por jogada, 3 rolos giram e param em sequência; chance de 1 em 25 de sair três iguais = $1.000. Funciona com teclado, mouse, toque e controle. No modo história fica fechado até ser liberado.
- **Aeroporto (v94):** hangar 3× mais fundo (em direção à pista), com porta voltada para o pátio; aviões do aeroporto com metade do tamanho.
- **Aeroporto (v93):** ciclo completo: o avião sai do hangar, taxia até a cabeceira, decola, faz a curva e some; ~12 s depois outro pousa, freia, taxia de volta e entra no hangar; ~14 s depois o ciclo recomeça (cerca de 1 min e meio por volta).
- **Aeroporto (v92):** prédio especial num quarteirão duplo (2 quadras), longe do centro: pista com marcações, taxiway, pátio, terminal com letreiro, torre de controle, hangar, um avião estacionado e cerca com cancela automática (a mesma da indústria). Um avião (mesmo modelo dos que cruzam o céu) decola, faz uma curva para um lado aleatório e some; depois outro pousa, freia e o ciclo recomeça. Nada controlável; ícone próprio no mapa.
- **Navios cargueiros (v91):** 2 navios no horizonte da praia, em pistas invisíveis a 150 m e 200 m da areia, em sentidos opostos; no fim do mapa param, giram e voltam. Containers com cores e pilhas aleatórias (paleta da indústria), casco de cor aleatória. Lanchas, jet skis e Vortex batem no casco; o helicóptero pousa no convés e dá para descer e andar nele (você e o helicóptero vão junto). Uma malha por navio (leve).
- **v90:** passageira da missão do píer fala pela barra de diálogo com retrato; menus 100% no controle (D-pad e analógico navegam, foco amarelo visível, ←→ ajustam sliders e listas, A confirma, B volta; CARREGAR SAVE entra na navegação).
- **Correção (história):** a 1ª missão não dependia mais do celular fora do modo avião, e agora chega com aviso "NOVA MISSÃO" + GPS apontando para o "!". Se a cidade não tiver a marina, usa outro píer ou a orla como destino.
- **Checagem de versão do save:** o .psave guarda a versão do jogo (`GAME_VER`, igual ao número da versão publicada; hoje v111). Ao carregar um save de outra versão (ou antigo, sem versão), aparece um erro e ele não é carregado. O número sobe a cada atualização entregue.
- **História: só o Jason na 1ª missão.** A troca de personagem fica bloqueada até liberar a casa segura.
- **Escolha do modo ao gerar cidade:** os botões HISTÓRIA/LIVRE saíram do menu. Ao clicar em GERAR NOVA CIDADE (ou GERAR COM ESTA SEED) abre uma janela com dois quadros em pixel art no estilo do seletor de personagem: Jason = modo história, Lucia = modo livre; preto e branco, colorindo o que estiver em foco. Escolher segue para o carregamento; Esc/○ volta ao menu.
- **História: casa segura trancada no início.** Só libera ao concluir a 1ª missão; então chega o aviso "vá até sua casa dormir" (toast + SMS da Lucia) e o ícone aparece no mapa. Antes disso a porta diz "CASA TRANCADA" e a garagem não funciona.
- **Base do modo história:** começo em ponto aleatório, mapa vazio só com o "!" da missão; recursos trancados (shopping, oficina, concessionária, Point Haze, fenda, synthwave, eventos, dupla) até missões liberarem (`STORY_MISSIONS`: needs/unlock/reveal, `storyOK`, `storyMap`, `storyComplete`). Missão 1 (carona até o píer) termina só com "MISSÃO CONCLUÍDA · +$X". Dicas aleatórias por SMS só no modo livre.
- **Pontes levadiças:** 2 por cidade, em pontes de pista dupla sem arco (nunca a do pedágio nem a da foz/borda). Trecho móvel = 1/3 da ponte, duas folhas até 45° com dobradiças e engrenagens visíveis por baixo. Ciclo 5 s sobe · 60 s aberta · 5 s desce · 60 s fechada. Trânsito reduzido (máx. 3 por ponte) e parado em fila antes da folha, sem tentar desviar; carros sobre a folha escorregam e podem cair. Procurado: sobem e o ícone vira X vermelho; guaritas nas duas cabeceiras (na calçada) forçam a descida ou levantam manualmente.
- **Mapa:** a legenda agora mostra só o que existe na cidade atual e inclui missão, área de busca da polícia, chuva, itens raros "?" e viaturas do radar; corrida e arrancada indicam o horário (22h–8h); ícones da legenda maiores. Os marcadores de rampage (caveira), corrida (bandeira quadriculada) e arrancada (carrinho com fumaça) no cenário viraram objetos 3D pequenos girando, em vez de ícones grandes virados para a câmera.
- **Vortex:** hovercraft anfíbio (terra e água, entra e sai do mar pela praia, desliza mais na terra). Sempre na areia ao lado do farol; reaparece 2 h de jogo depois de levado.
- **Oficina: turbo e neon:** turbo ($1.500) dobra a velocidade final; neon embaixo do carro ($300, trocar cor $50) com 8 cores ou cor livre, feito como brilho no chão (sem luz real). Salvos no carro e na garagem. Removido o aviso "serviços grátis".
- **Salvar na cama:** deitar na cama da casa segura abre o download do save; ao carregar, o jogo começa na casa segura.
- **Eventos pelo mapa:** RAMPAGE (caveira; demogorgons infinitos com 3× a vida, arma do ponto com munição infinita, 90 s), CORRIDA (bandeira quadriculada; ilegal, só das 22h às 8h; checkpoints contra 2 rivais) e ARRANCADA (carro com fumaça; só das 22h às 8h, exige nitro, 1 rival). Ícones no radar e no mapa; cada ponto volta depois de um tempo.
- **Novos veículos:** perua, crossover, compacto e roadster (variações de sedã, SUV, hatch e conversível) e jet ski (mais rápido que a lancha, chega rente à areia; parado na praia e ao lado do píer, alguns andando no mar). Todos na concessionária. Lanchas do rio agora colidem com lanchas e jet skis.
- **Menu de pausa:** botão CONTINUAR trocado por um ✕ no canto (Esc continua funcionando); SALVAR JOGO aparece à esquerda de CARREGAR SAVE; saiu o aviso "o jogo não salva sozinho". O seletor HISTÓRIA/LIVRE fica na linha de CONFIGURAÇÕES e só vale ao gerar uma cidade nova; o save guarda o modo da partida.
- **Modo história × livre:** seletor no menu inicial. No modo história, a primeira missão é um SMS opcional pedindo carona até o píer; no desembarque a passageira fala de uma transmissão vinda do mar (pista para Point Haze). O SMS volta no dia seguinte se ninguém atender. A dica de SMS sobre a lancha virou charada.
- **Jason e Lucia juntos:** chamar o outro na casa segura ou entrar no carro onde ele ficou. No carro, Alt troca o controle na hora: motorista dirige e o parceiro atira na polícia (70%); atirador atira e o parceiro dirige sozinho (GPS ou passeio/fuga), carro 70% mais resistente. Bullet time do Jason de carona; câmera lenta da Lucia dirigindo.
- **Correções:** plataforma da concessionária sem z-fighting; árvores não nascem mais dentro das garagens (casa segura e DeLorean); alvo do paraquedas paga por anel ($60/$150/$300); moto inclina com as rodas.
- **Concessionária Pixel Motors:** showroom com estacionamento e plataforma giratória (ícone de carrinho no mapa). O vendedor abre um menu com o veículo girando, troca de modelo e cor, e compra. Todos os 14 veículos aparecem com preço ($1.200 a $25.000), mas só se compra o que cabe na garagem. O carro comprado ocupa uma vaga (a mais antiga é substituída) e você sai dirigindo; comprar outro em seguida tira o anterior da rua. A garagem agora é a sua frota: o carro sai e continua seu; se sumir, volta para a vaga; destruído, libera a vaga. Carro roubado guardado substitui o que estava fora.
- **Documento e blitz:** carros comprados são legais. Na blitz, carro roubado é sempre descoberto: 50% de prisão, 50% de liberação.
- **Economia rebalanceada:** táxi $15 + distância/10; vigilante $150 por nível; conveniência $120–260; lojas do shopping $120–280; penhor paga 60% do valor; atropelamento $0–20; Upside Down $1.500; alvo do paraquedas $150. Custos: hospital ao morrer 10% do dinheiro ($100–1.000), fiança 15% (mínimo $500), roupa $25, lanche $20, pintura $100, nitro $500. Removida a dica falsa de roubar banco.
- **Micro-ilha com pedágio**: toda cidade gerada tem 1 quarteirão residencial cercado de água (os canais novos se ligam ao rio e as lanchas da IA navegam em volta), com uma única ponte de pista simples (uma faixa para cada lado, mesmo que a rua seja avenida). No máximo 2 carros na ponte; cada carro para 2 s na cancela, ela abre e ele segue. Na ponte há guarita com atendente ("São 10 dólares, amigo." / "Obrigado! Boa viagem.") e duas cancelas: com $10 ela abre e cobra; sem dinheiro não abre; furar a cancela = ★. Na ilha fica a casinha com garagem coberta de 1 vaga e o DeLorean dentro. As garagens "Back to the Past" espalhadas pelo mapa saíram. DeLorean levado ou destruído: outro aparece 3 h de jogo (3 min) depois, quando você estiver longe.
- **Polícia em 3 níveis** (estrelas amarelas no lugar da faixa "PROCURADO"): ★ 1 viatura; ★★ 2 viaturas, que atiram; ★★★ 2 viaturas e helicóptero da polícia, que segue de cima e atira. Todos acertam 40% dos tiros. Explodir 3 coisas durante a fuga sobe um nível; pegar helicóptero durante a fuga vai direto para ★★★. Na água vem a lancha da polícia (azul, giroflex, sirene e tiros), 2 lanchas no ★★★. Policiais a pé também passaram a acertar 40%.
- **Blitz** (só em rua de mão única): as 2 viaturas ocupam uma faixa e os cones na divisória levam o trânsito para a outra. O trânsito no trecho fica limitado a no máximo 2 carros. Um policial fica no meio da rua e põe um cone na sua frente quando você chega; o outro caminha até a janela. Depois de uma perseguição, se você ainda bate com a descrição (só a roupa ou só o carro iguais): "Deixe eu ver seus documentos." → "Eu acho que te reconheço…" → 50% de ser preso (com os dois iguais, preso). Blitz de rotina: "Documentos, por favor." → "Ok, tudo em ordem. Pode seguir." Liberado, o cone sai da frente. Furar a blitz = ★★.
- **Helicóptero na delegacia** com pintura de polícia (azul-marinho, faixa branca e giroflex).
- **Point Haze de helicóptero**: voando 300 m mar adentro você chega à ilha, e a polícia é despistada. Lá não tem heliponto, mas dá para pousar e decolar à vontade, e voltar voando.
- **Barro voando nas poças de lama**: ao passar pelas poças na estrada de terra molhada, as rodas traseiras jogam barro marrom para trás e para cima, com mais força acelerando e muito mais quando o carro está atolando (roda girando em falso).
- **Modo avião no celular**: com as notificações desligadas aparece um aviãozinho no lugar do sinal. Também ficou pronto o código das futuras mensagens de missão, `phoneMission(texto)`: aparecem com envelope vermelho-alaranjado no minimapa e "!" laranja na lista, e não chegam no modo avião.
- **Pânico com arma na mão**: a pé na rua, os pedestres num raio de ~18 m fogem como na chuva, e alguns gritam ("Ele tá armado!", "Alguém chama a polícia!"). Se o pânico durar 1 h de jogo (1 min real), a polícia vem.
- **TV (Pixel News)**: câmera do helicóptero mais perto (tempestade ~42 m, perseguição ~46 m). Ela sobe acima dos telhados e gira para achar ângulo livre quando um prédio tapa a vista. Os carros da perseguição não somem nem ficam invisíveis enquanto a TV está ligada. Quando o bandido morre, a cena fica 6 s no ar e logo começa outra perseguição.
- **Troca de personagem com um deles na Point Haze**: a câmera sobe só 55 m lá, sem mostrar a linha de espuma da borda.
- **Tiros**: pedestres agora aguentam 5 tiros normais (antes 3). Tiro na cabeça, Colt Magnum e bazuca continuam matando na hora.
- **Polícia (regras)**: sem testemunha, atirar à toa não dá nada. Matar 10 pedestres ou explodir 3 veículos chama a polícia mesmo sem viatura por perto, e matar alguém em lugar fechado também.
- **Assalto em qualquer loja do shopping** (mesmas regras da conveniência): mire no vendedor por 3 s, pegue o dinheiro, e a polícia espera na saída. A loja fecha e só reabre 3 h de jogo (3 min) depois do fim da perseguição, da morte ou da prisão. A conveniência do posto também fecha nesse período.
- **Limpeza de veículos abandonados**: carro ou moto que você usou e largou some 1 h de jogo depois (1 min real), sempre a mais de 50 m de você. Não somem: carros da garagem, o carro do outro personagem, o carro do prêmio dos discos, táxi, serviços e lanchas. Helicóptero largado fora do heliponto (ex.: num telhado) volta para o heliponto depois de 1 h de jogo, quando você estiver longe.
- **Táxi com luminoso de verdade**: no teto, um trapézio amarelo com "TAXI" escrito na frente e atrás, no lugar da bolha oval.
- **Corrigido: helicóptero pulando ao acelerar.** A oscilação de pairar dependia da posição X, então em velocidade virava um sobe e desce rápido. Agora a oscilação é suave e independe da velocidade.
- **Cheats por personagem**: armas, vida, colete e os cheats pessoais (vida infinita, munição infinita, nunca procurado) valem só para quem digitou. Cada personagem guarda as próprias armas, vida e colete. Cheats de mundo (tempestade, polícia, explodir carros, discos) afetam os dois. Qualquer cheat impede os dois de salvar.
- **Sons do celular**: tom de chamando… e depois um bipe positivo (atendeu) ou negativo (recusado). Ligações são recusadas quando você está fugindo da polícia, e número inexistente também dá recusa.
- **Táxi**: câmera livre durante a corrida (mouse ou analógico direito) e **pular viagem** com T (↓ no controle): fade e você já desce no destino, pagando a corrida.
- **Ajustes de interface**: balões de fala mais baixos, mais perto da cabeça. No shopping saiu o balão de comando em cima do vendedor; ficou só o cumprimento, e o comando aparece embaixo da tela, como na conveniência. A bomba de combustível continua com o balão. Eletrônicos e Malas & Mochilas Co. foram para o 2º andar. O guarda-roupa só mostra headphone e mochila nas cores já compradas.
- **Aviso de PIXel**: quem recebe, ao virar o personagem ativo, ganha a notificação "JASON te enviou um PIXel de $X!" e a mensagem fica no celular.
- **Detalhes de bairro**: nas zonas residenciais, algumas árvores têm bola ou frisbee preso na copa (somem se a árvore cair) e alguns fios de poste têm um par de tênis pendurado pelo cadarço.
- **Corrigido: poeira marrom atrás da lancha no mar.** O mar longe da cidade era tratado como "zona rural", e por isso soltava a poeira de estrada de terra. Barcos e veículos na água não soltam mais poeira, nem sofrem o efeito da terra.
- **Fuga da cela**: pena de 5 minutos. O guarda anda em U pelo corredor e some pela porta por 7–14 s. Depois de 1 minuto, o colega de cela (balão: "Usa a colher pra cavar um túnel de fuga") te dá uma colher. No canto marcado da parede, clique/E/R (R2/□/✕ no controle) com o guarda fora da vista: 30 s de cavação. Pego cavando, a pena volta para 5 minutos. Com o túnel pronto, você sai num beco perto da delegacia, longe das armas e do portal.
- **Câmera pro céu nas trocas de mundo** (estilo GTA V): ao trocar Jason/Lucia entre cidades diferentes e ao ir ou voltar da Point Haze e do Upside Down, a câmera faz a mesma vista de cima da troca no mesmo mundo: olhando reto para baixo, sobe até a mesma altura da troca no mesmo mundo e a tela escurece. Depois do loading, clareia lá de cima e a câmera desce reta até o personagem.
- **Chegada da viagem no tempo sem pausa**: o jogo congelava a física durante o fade de saída e a explosão de chegada. Agora é o inverso da ida: o carro espera parado e invisível; no flash da explosão ele surge e já sai andando a 88 km/h.
- **Balões de fala em pixel art** ligados às ações: vendedores do shopping ("Olá, amigo! O que deseja?"), conveniência ("Obrigado e volte sempre!" / no assalto "Por favor, poupe minha vida!"), dono da casa de penhores, cachorro bravo, paramédico do 192, taxista, motorista do carro roubado, pedestre baleado, polícia ao começar a perseguição e o outro personagem na casa segura.
- **Barra de diálogo com retrato** (pausa o jogo, texto letra por letra, escolhas): código pronto em `dlgOpen()` para missões futuras, ainda sem uso no jogo.
- **Sem stutter ao anoitecer, em explosões e na bazuca**: as luzes (postes, faróis, explosão e as lâmpadas da oficina e do posto) agora ficam sempre na cena, apagadas com intensidade 0. Trocar a quantidade de luzes recompilava todos os shaders. No loading, o jogo também prepara as partículas de fogo e fumaça, o foguete da bazuca, o carro queimado, o bloom e o céu da noite.
- **Celular legível**: tela e teclas em alta resolução com texto normal (não pixelado), e todo texto ajustado para caber na tela.
- **Assalto a residências** (22h–8h): setas em casas aleatórias do bairro residencial. São 5 interiores, versões da casa segura com cores diferentes e espelhadas. Você tem 10 s para pegar TV, micro-ondas, DVD ou celular (de $20 a $150 cada, total no canto da tela); depois disso a polícia vem. Algumas casas têm cachorro bravo que morde.
- **Casa de penhores**: uma por cidade, seta escondida num beco longe das armas. Depósito com prateleiras empoeiradas e dono no balcão; E/→ vende tudo. Mais de 10 s lá dentro atrai a polícia.
- **Polícia testemunha**: ela só vem se vir você roubar carro ou atirar, a até meio quarteirão (38 m) de uma viatura ou policial.
- **Becos**: caixas, sacos, pneus, barris e paletes quebram só de esbarrar, a pé ou de carro. A caçamba grande precisa de batida acima de 4. Gatos reduzidos pela metade (no máximo 2 ao mesmo tempo).
- **Controle no padrão GTA V (PS4)**: ↑ abre o celular (a pé e no carro); → a pé interage (loja, guarda-roupa, paciente) ou chama um táxi que passa perto, como no GTA V; segurar ↓ troca de personagem. COMANDOS → CONTROLE e o FAQ CELULAR/SMS foram atualizados com o passo a passo do celular e de como chamar táxi, ambulância e polícia. A aba de toque passou a se chamar TOQUE (MOBILE).
- **Carteira por personagem e app PIXel**: Jason e Lucia têm dinheiro separado. No celular, o app **$ PIXel** manda dinheiro para o outro: o valor é digitado no teclado do celular, LIGAR envia e APAGAR corrige ou volta. Saves antigos: o personagem em uso fica com todo o dinheiro.
- **Compras por personagem**: Jason e Lucia têm guarda-roupa próprio. Roupas, acessórios, headphone e mochila comprados por um não passam para o outro. O celular também é por personagem. Tudo fica salvo no save.
- **Limite de munição e mochila**: sem mochila, até 150 balas por arma e 3 foguetes; acima disso a arma no chão não é pega. Nova loja **Malas & Mochilas Co.** no shopping (layout da conveniência, prateleiras de malas): mochila de $500 em todas as cores da roupa, menos laranja. Com ela o limite vai a 1.500 balas e 30 foguetes. A mochila substitui a laranja do paraquedas nas costas, e dá para tirar ou colocar no guarda-roupa. Tirando, a munição é cortada para o limite.
- **Discos de vinil (colecionáveis)**: 15 por cidade, entre o lixo dos becos e 3 nos rios (precisa de lancha). Aparecem como "?" no minimapa. Uma única textura de capa e de disco é gerada e compartilhada por todos. Com os 15: armas com munição máxima e colete na porta da casa segura (reaparecem quando você se afasta) e um esportivo com nitro sempre na porta. Cheat **COLLECTTHEMALL** completa a coleção, mas o jogo deixa de poder ser salvo.
- **Celular** (P / ↑ no controle, também dentro de veículos): pixel art com tela e teclado; números discam direto e, subindo, você entra na tela. 190 chama a polícia (só persegue se vir crime), 192 chama a ambulância com giroflex (o paramédico enche a vida até 100), 555 chama um táxi. 3 modelos (PIXDROID S, iPIXEL 15, TIJOLÃO 3310); Jason começa com Android e Lucia com iOS, e o modelo fica salvo por personagem.
- **SMS de dicas**: uma a cada ~5 min (ordem e intervalo aleatórios, só dicas de gameplay), com envelope no minimapa e bipe-bipe; ficam marcadas como lidas e somem após 24 h de jogo. Dá para desligar em CONFIG (engrenagem) no celular.
- **Loja de eletrônicos** no shopping (layout da conveniência, prateleiras de eletrônicos): vende celulares e **headphone** (sprite na cabeça, 6 cores). Com o fone, as rádios tocam a pé (Q, vírgula/ponto; ← no controle); tirar o fone no guarda-roupa para a música.
- **FAQ** ganhou as abas CELULAR/SMS, MECÂNICAS, MISSÕES e AMBIENTE.
- Missão PARAMÉDICO: numa ambulância, T começa. Vá até o ferido (deitado, com sangue, seta vermelha), desça perto dele com a ambulância a até ~14 m e aperte E (ou → no controle) para socorrer; volte à ambulância e leve ao hospital. Cada paciente salvo paga ($50 + bônus por tempo + $10 por paciente já salvo no turno) e o próximo chamado vem em seguida. Se o tempo acabar, o paciente não resiste e vem outro chamado. T encerra.
- Ambulâncias de rua: de vez em quando uma passa em alta velocidade com giroflex piscando, sem parar em semáforo (mais raras que a polícia). Na ambulância, o toque curto na buzina alterna: desligado → giroflex → giroflex + sirene → desligado. A sirene é opcional (a missão começa só com o giroflex). As ambulâncias de rua passam com a sirene ligada.
- Monitor de desempenho (F3/MONITOR) agora fica no canto superior esquerdo, para não cobrir o seletor de personagem.
- Becos mais cheios: além dos sacos de lixo, agora há caixas de papelão (às vezes empilhadas), engradados de madeira, pilhas de pneus, tambores coloridos e paletes, encostados nas paredes. Tudo no beco é quebrável/derrubável pelo carro. Nem todo beco tem caçamba; ela segura batidinha (abaixo de ~20 km/h) mas uma batida mais forte a estoura em pedaços e ela some. Gato em cima da caçamba está seguro, mas se ela quebrar ele cai no chão e foge, exposto.
- Corrigido: z-fighting em caçambas de beco — às vezes duas caçambas eram geradas uma dentro da outra (faces coincidentes piscando). Agora ficam sempre separadas.
- Cães e gatos em pixel art, no mesmo estilo dos pedestres (6 pelagens de cão, 5 de gato). Gatos vivem nos becos e não saem para a calçada: andam entre as caçambas e de vez em quando sobem e ficam em cima delas. Cães aparecem nos quintais das casas, na areia da praia e, de vez em quando, nas calçadas. Fogem de quem chega correndo ou de carro rápido e podem ser atropelados. Até 8 por perto (4 no celular); não existem no Upside Down nem em Point Haze.
- Ambulâncias: 3 estacionadas na frente das alas de cada hospital, de frente para a rua. É a van, branca, com faixa e cruz vermelhas nas laterais, cruz no teto e giroflex vermelho/azul. Dá para pegar e dirigir; o heliponto do hospital não ocupa o lugar delas.
- Táxi: G (ou ↑ no direcional, a pé) chama o táxi mais próximo do quarteirão; ele encosta, você segura F para entrar e marca o destino no mapa. Detalhes na seção Táxi.
- Mapa no controle: o analógico move uma mira, A/✕ marca o destino e B/○ fecha.
- Nenhum cheat funciona durante a troca de personagem (câmera subindo, deslizando e descendo), a troca de mundo ou a viagem no tempo; aparece CHEAT BLOQUEADO e o código digitado é descartado.
- Teleporte (cheat) e troca de personagem ficam bloqueados nos momentos que podiam quebrar o jogo: morto/afogando, nocauteado, saltando de paraquedas, vendo TV, DeLorean com o portal aberto (≥ 70 km/h) ou viajando no tempo, durante transições de mundo, no farol, em salto de rampa, decolando/pousando o helicóptero e dentro de interiores. O teleporte também não funciona de dentro do helicóptero. Um aviso diz o motivo; o marcador do teleporte continua no mapa.
- Não dá para trocar de personagem durante uma perseguição, preso na delegacia, dentro da loja do posto ou do shopping, nem com qualquer menu aberto (guarda-roupa, loja, mapa, configurações, rodas): o seletor fica apagado.
- Corrigido: depois de afogar/morrer e ser levado para outro lugar, a tela podia ficar em preto e branco.
- "Mundo Invertido" agora se chama **Upside Down** (nome em inglês, como SUNSET SHORES, SYNTHWAVE e POINT HAZE). A pasta da trilha pode ser `radios/Upside Down` (o nome antigo ainda funciona).
- Paraquedas: os prédios têm colisão (bater na parede faz descer raspando nela) e dá para pousar em qualquer telhado. No telhado você anda e salta de novo pela borda com E. O comando foi invertido: ↓ planar, ↑ descer mais rápido.
- Helicóptero: barulho de motor, rádio (Q e roda do mouse, como no carro) e pouso em telhados (prédio largo o bastante e você centralizado). Descendo no telhado, você fica nele e pode saltar de paraquedas pela borda. Explosão do helicóptero não derruba mais quem está lá no alto de paraquedas.
- Persistência de Jason e Lucia (detalhes na seção Personagens).
- Corrigido: em Point Haze, aves e helicópteros/aviões do céu piscavam e sumiam (as aves eram escondidas e reexibidas conforme a tempestade oscilava). A ilha agora não tem tráfego aéreo nem aves, e no resto do jogo as aves não piscam mais na transição da tempestade.
- Corrigido: a lancha soltava "nuvem de areia" (fumaça de pneu) junto com o respingo na água.
- Corrigido: dentro dos interiores (shopping, loja, casa segura, delegacia), na câmera de cima e na isométrica, uma faixa do piso sumia (o corte em cilindro na direção da câmera cortava o próprio chão). Agora o corte esconde só o que está acima da cabeça do jogador (teto, mezanino, alto das paredes), também na câmera de cima, e esses elementos não fazem sombra.
- Corrigido: voar de helicóptero (ou de paraquedas) sobre rio/mar matava o jogador afogado. Desembarcar sobre a água continua afogando.
- Colete à prova de balas: faixa branca fina embaixo da barra de vida, na metade direita (ao lado da azul do especial). Absorve o dano antes da vida (tiros, explosões, quedas, monstros). Achado em alguns becos e na porta da delegacia (esse volta 2 min depois de pego). Ícone: colete escuro estofado, sem mangas, com alças e cinta. HESOYAM enche o colete também. Morrer zera o colete; o save guarda.
- Lucia agora troca de roupa no guarda-roupa e na loja, como o Jason (cores, óculos, colar etc.).
- Jason e Lucia: troca de personagem estilo GTA V, com especial de cada um (bullet time do Jason a pé com arma; câmera lenta da Lucia dirigindo). Detalhes na seção Personagens.
- Helipontos e o estacionamento do arranha-céu ficam dentro do quarteirão, sem avançar na calçada nem em cima de árvores e postes.
- Helicóptero pilotável: helipontos com helicóptero no chão, na área livre do quarteirão da delegacia, do hospital e do arranha-céu (o pátio do arranha-céu ganhou também um estacionamento com carros). Detalhes na seção Helicóptero.
- Câmera sobre o ombro (TPS): em 3ª pessoa a pé, com uma arma na mão, a câmera vai para trás do ombro direito e aparece uma mira no centro da tela; o tiro sai para onde a mira aponta. De punhos, volta a câmera normal de 3ª pessoa.
- Arma na mão: o jogador segura a arma escolhida, usando o mesmo modelo do ícone flutuante, em tamanho reduzido, ao lado da mão direita (3ª pessoa e câmera de cima). Em 1ª pessoa não aparece, para não tapar a visão.
- Point Haze: o medidor de distância saiu; o jogador descobre a ilha indo além-mar.
- Rádio por mundo: a pasta do mundo (Synthwave, Upside Down, Point Haze) é a prioridade: entra sozinha, em sequência (ordem dos arquivos), mesmo com a KRFM ao vivo escolhida. As rádios comuns continuam na roda para trocar se quiser dentro do veículo; a pé volta sozinho para a trilha do mundo e, ao entrar num veículo, volta a rádio que estava tocando nele. O som dos carros com som alto só existe no Modern.
- Aviso do Chrome sobre getImageData (willReadFrequently) resolvido.
- Paraquedas: mochila laranja nas costas, desenhada no personagem como os óculos. Aparece ao subir no terraço de salto e some ao pousar. Os paraquedistas NPC também usam.
- Roupa de praia: no guarda-roupa/loja há a categoria SUNGA (várias cores), a opção sem camisa (✕ em CAMISA) e descalço (✕ em CALÇADO). Dá para andar de sunga pela cidade. Os banhistas (cangas, espreguiçadeiras e quem caminha na areia) usam sunga ou biquíni, sem camisa e descalços.
- Espreguiçadeiras: o banhista deitado agora fica com a cabeça no encosto.
- Setas amarelas e interiores: toda entrada grava a origem (qual interior, qual porta e o ponto de saída) e a saída devolve sempre para ela. Vale para as lojas dos postos, shopping, casa segura (inclusive o castelo de Point Haze) e delegacia. Cada porta tem um código (`gas:<quarteirão>`, `mall`, `safe`, `safe:haze`, `pol`, `pol:preso`), base para missões futuras do tipo "mesmo interior, porta diferente". O save feito lá dentro também usa essa origem.
- Mapa completo: o nome da região aparece no topo, com uma fonte por mundo (Sunset Shores em letra de praia no Modern, neon retrô no Synthwave, terror no Upside Down, pirata em Point Haze). A legenda desceu para dar espaço; em Point Haze ela mostra só GPS, casa segura e praia.
- **Point Haze (novo mundo paralelo):** ilhota deserta 3×3 quarteirões. Pegue uma lancha em Sunset Shores e siga 300 m mar adentro; um medidor (0–300 m) aparece e, ao completar, a tela escurece, carrega e você chega de lancha perto do único píer da ilha. Na chegada, qualquer nível de procurado é zerado na hora. Para voltar, saia 300 m da praia da ilha com a lancha do píer.
- Lama nas estradas de terra: as poças de chuva da terra viraram lama marrom e opaca, sem reflexo, mais escura no miolo. Elas substituem os antigos atoleiros redondos. A aderência cai conforme a profundidade; carros pequenos atolam, e caminhões e camionetes passam.
- Corrigido: as poças da estrada de terra ficavam por baixo do decalque da terra e nunca apareciam.
- Letreiros dos marcos: ficam só as placas oficiais "... DE SUNSET SHORES". O neon POLÍCIA da delegacia, que disputava o mesmo lugar com a placa e alternava com a distância, saiu, e a placa voltou ao painel da fachada.
- Pular música: `.` / `,`, ↑ no controle e botão MÚSICA no celular passam a faixa dentro da rádio atual. Q rápido e a roda do mouse trocam de rádio. Cada rádio começa numa música sorteada a cada sessão.
- Rádios por pasta: cada subpasta de `radios/` é uma rádio e a roda mostra só os nomes das pastas. Pastas `Synthwave` e `Upside Down` viram a trilha do mundo correspondente, que entra sozinha e toca também a pé.
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
- Upside Down com até dez demogorgons, perseguição, saltos e pontos vermelhos no mapa.
- Ônibus com letreiros de destino: CENTRO, PRAIA e INDUSTRIA.
- Chuva regional sem preferência pela posição do jogador; aves desaparecem na chuva e paraquedistas NPC são retirados na chuva forte.
- Viaturas estacionadas na delegacia.
- Suspeitos revidam nas perseguições ambientais; viaturas destruídas podem ser substituídas por reforços.
- Oficina cobra pintura, instalação de nitro e reparos. Casa e troca de roupas já adquiridas continuam gratuitas.
- Dinheiro de pedestre atropelado só pode ser coletado a pé.
- Terraço de salto reservado pela seed, com seta amarela e mini paraquedas no mapa; caminhada no teto e salto pelas quatro bordas.
- Controle do paraquedas com curvas, planeio prolongado e descida acelerada; alvo na praia paga $60 (borda), $150 (anel do meio) ou $300 (na mosca) sem cheat.
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

Uma partida nova começa em **Modern**, com câmera de terceira pessoa. Synthwave e Upside Down fazem parte dos segredos do jogo; um save pode restaurar o estilo em que foi salvo.

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
| Q rápido | Próxima rádio |
| . / , | Próxima / anterior música dentro da rádio atual |
| Roda do mouse no carro | Trocar de rádio |
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
| D-pad ↑ / ↓ | Próxima música da rádio / missão |
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
- **Lama nas estradas de terra:** com chuva, as estradas de terra ganham poças de lama no mesmo padrão aleatório das poças da rua, só que marrons, opacas e sem reflexo, com o miolo escuro clareando para as bordas. Elas crescem com a chuva e secam devagar depois.
- A lama reduz a aderência de todos os veículos conforme a profundidade: o miolo escuro freia e escorrega mais que a borda rasa. Carros pequenos atolam no miolo; vans atolam menos; caminhões, camionetes, SUVs e ônibus passam, só escorregando um pouco. Com chuva, é normal o trânsito travar nesses trechos.
- A lama aparece mesmo com o reflexo desligado (o reflexo continua controlando só as poças da rua e da calçada).

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

## Personagens: Jason e Lucia

- O jogo começa com **Jason** (o visual de sempre, que troca de roupa no guarda-roupa e na loja). **Lucia** começa com o visual dela e também troca de roupa no guarda-roupa e na loja.
- **Bloqueios:** com a polícia atrás, na delegacia, na loja do posto, no shopping ou com qualquer menu aberto, a troca fica bloqueada e o seletor apagado.
- **Trocar:** segure **Alt** (teclado) ou **↓ no direcional** (controle) para abrir o seletor no canto inferior direito; **←/→** (ou A/D, ou o analógico) escolhe; soltar troca. Também dá para clicar/tocar na metade do círculo. Um toque curto em ↓ no controle continua iniciando missão.
- **A troca:** a câmera fica de cima, sobe ao céu, desliza pela cidade e desce onde o outro personagem está (um ponto aleatório da cidade). Se estava de carro, o carro fica para trás. O nível de procurado não passa de um para o outro.
- **Especial (Caps Lock ou L3+R3):** desacelera o jogo. **Jason:** bullet time, só a pé e com arma na mão. **Lucia:** câmera lenta, só dentro de veículo. Vale em todos os mundos.
- **Barra do especial:** a faixa azul fina embaixo da barra de vida (metade da largura). Enche sozinha (cheia a cada 3 h de jogo, 3 min reais), dura cerca de 10 s cheia e pode ser ligada e desligada à vontade para economizar. Desliga sozinha se acabar ou se a condição deixar de valer. Cada personagem tem a sua.
- **Persistência:** quem fica para trás continua onde estava (a pé, no carro, no helicóptero parado no ar, no telhado, na casa segura) por **5 h de jogo (5 min)**. Volte para ele dentro desse prazo e ele está lá; o carro só some se for destruído. Passado o prazo, ele volta para a calçada da cidade inicial (Sunset Shores, no Modern).
- **Outros mundos:** se o outro personagem estiver em outro mundo (Synthwave, Upside Down, Point Haze ou a cidade inicial), a troca recarrega aquele mundo.
- **Casa segura:** entrando nela, o outro personagem está lá dentro (se não estiver no meio de alguma coisa, dentro das 5 h). Trocar ali é na hora, sem a câmera subir. Trocar com o outro a menos de ~45 m também é só um pulo.
- O save guarda quem está ativo, o visual do Jason e as duas barras.

## Táxi

- **Chamar:** **G** no teclado ou **↑ no direcional** do controle (a pé). Vem o táxi mais próximo dentro de ~1 quarteirão; se não houver, aparece um aviso. Procurado não consegue táxi.
- **Embarcar:** o táxi encosta na rua ao seu lado. **Segure F** (ou Y/△) para entrar como passageiro. Um toque rápido continua sendo o "roubar o carro" normal.
- **Destino:** o mapa abre sozinho. Mouse: botão direito marca. Celular: toque longo. Controle: analógico move a mira amarela, **A/✕** marca, **B/○** fecha. Se já houver um marcador, ele vai direto.
- **Corrida:** o táxi dirige pelas ruas até o destino e encosta. Rádio funciona como no carro.
- **Preço:** $5 de bandeirada + $1 a cada 10 m. Sem dinheiro, sem corrida; se o dinheiro acabar no caminho, a corrida termina ali.
- **Descer:** F a qualquer momento encerra a corrida.

## Helicóptero

- **Onde:** helipontos (quadrado escuro com borda amarela e H branco) na área livre dos quarteirões da delegacia, do hospital e do arranha-céu. No arranha-céu, o pátio ao lado virou estacionamento.
- **Embarcar:** E perto do helicóptero.
- **Decolar:** ↑ (W). Ele sobe sozinho até a altitude fixa de voo, acima dos prédios e abaixo dos helicópteros que cruzam o céu.
- **Voar:** ↑/↓ acelera e freia, ←/→ vira. Não há controle de altura. Dá para voar pelo mapa inteiro e um pouco além do mar.
- **Pousar:** E em qualquer lugar; ele desce na vertical. Não pousa na água nem em cima de prédio. No chão: E desembarca, ↑ decola de novo. O helicóptero fica onde você deixou.
- **Saltar de paraquedas:** ESPAÇO no ar. Você salta com a mochila laranja e controla o paraquedas como no salto do terraço. O helicóptero é abandonado, cai bem mais rápido e explode no chão (na água, só afunda). Um helicóptero destruído volta ao heliponto depois de uns 2 minutos, quando você estiver longe.

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
| ↓ / S ou analógico para trás | Puxa: reduz a descida e aumenta o alcance |
| ↑ / W ou analógico para a frente | Inclina para baixo e acelera a descida |
| Sem entrada | Mantém direção e planeio normal |

No terraço, o direcional continua servindo para caminhar. No ar, o comando para cima prolonga o planeio, sem permitir subir indefinidamente. O paraquedas tem inclinação suave durante essas manobras.

### Alvo e NPCs

- Ao saltar, surge um círculo vermelho na areia. Pousar a até aproximadamente **3,1 m** do centro rende **$60 a $300** conforme o anel, desde que a partida não tenha usado cheat.
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
- Piso molhado e terra alteram a aderência; as poças de lama das estradas de terra reduzem aderência e tração conforme a profundidade.
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
- Loja de conveniência com interior, caixa e produtos. Lanche de **$20 recupera 50 de vida**.
- Ameaçar o caixa com arma inicia assalto; violência aciona alarme e reação policial. Não é permitido entrar estando procurado.

## Personagem, armas e dinheiro

- Personagens em sprites procedurais de **32×48 pixels**, com animação direcional, roupas, rosto e acessórios.
- Pedestres caminham, conversam, olham vitrines, entram/saem de edifícios, fogem e reagem à chuva e à violência.
- Pulos sobre obstáculos baixos e possibilidade de subir em carros baixos.
- Punhos, pistola, Colt Magnum, metralhadora e bazuca; seleção direta ou por roda.
- Pistola/metralhadora exigem vários acertos no corpo; tiros na cabeça são letais. Magnum causa dano alto e tem cadência menor; bazuca causa explosão em área.
- Drive-by, danos em veículos e reação policial aos disparos.
- Armas, munição e kits de vida encontrados nos becos e no cemitério.
- Pedestres atropelados podem deixar **$0 a $20**. Quando o valor é zero, nada aparece; o dinheiro deixado fica disponível por tempo limitado.
- Esse dinheiro de atropelamento só é recolhido **a pé**, sem entrar no raio de coleta com carro, moto ou lancha. O evento de corpo boiando mantém sua coleta específica de barco.
- Coletável de dinheiro em formato de cifrão 3D, com tamanho reduzido.
- Dinheiro usado em combustível, reparos, comida e roupas, além de ser recebido por missões e coletáveis.

## Point Haze

- **Como chegar:** de Sunset Shores (Modern ou Synthwave), numa lancha, afaste-se 300 m da praia. A volta é igual: 300 m para fora da praia da ilha, chegando de lancha na costa de Sunset Shores, no mesmo trecho de onde saiu e no mesmo estilo (Modern ou Synthwave).
- **A ilha:** 3×3 quarteirões gerados pela mesma mecânica da cidade, com seed derivada da seed da cidade (cada cidade tem a sua ilha). Ruas de terra; o miolo é grama marrom-clara; em volta, 100% praia selvagem de areia encardida, sem guarda-sóis, cadeiras ou barracas, com a linha d'água irregular.
- **Cenário:** árvores mortas e retorcidas (as do cemitério) e pedras grandes soltas entre elas e na areia. No quarteirão central há um castelo em ruínas, que é a casa segura (porta ao sul). Na ilha não há veículos, NPCs, polícia nem trânsito: tudo é a pé. A única lancha é a do píer.
- **Clima:** sempre encoberto e com névoa (a mesma do cemitério). Com a chuva ligada, chove com frequência e as tempestades são bem mais prováveis.
- **Procurado:** chegar à ilha elimina qualquer nível de procurado, independente de roupa ou veículo.
- **Morte:** você acorda nas ruínas do castelo.
- **Save:** salvar na ilha guarda também de onde você veio, para que a volta leve à sua cidade.
- **Trilha:** a pasta `radios/Point Haze` é a OST da ilha.

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

**Portas e interiores:** os interiores são reaproveitados (todas as lojas de posto usam o mesmo cenário, por exemplo). Ao entrar por uma seta amarela, o jogo guarda o interior, o código da porta e o ponto de saída, e ao sair você volta exatamente para a porta por onde entrou. No código, `doorCode()` retorna a porta usada (`gas:<quarteirão>`, `mall`, `safe`, `safe:haze`, `pol`, `pol:preso`).

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
- Poças de água e anéis de gotas próximos da câmera no asfalto. Nas estradas de terra, as mesmas poças viram lama marrom, sem reflexo.
- **Reflexos simulados**, com cores do céu e rastros de luz: não há uma segunda renderização completa da cidade como no espelho das versões antigas.
- Calçadas usam tratamento mais simples; efeitos distantes são reduzidos.
- Opção para desligar o reflexo das poças em CONFIGURAÇÕES → GRÁFICOS. A lama das estradas de terra continua aparecendo, porque também afeta a direção.

## Segredos e mundos alternativos

### BACK TO THE PAST / Top Secret

Nas garagens especiais há um carro cinza inspirado no DeLorean, associado à viagem entre **Modern e Synthwave**.

- Carroceria e detalhes revisados: placa sobre o capô e barras laterais flutuantes removidas; barrinhas traseiras ajustadas ao vidro.
- Contornos de energia **ciano e rosa nos dois lados**, próximos à carroceria.
- **40 km/h:** contornos começam a acender.
- **70 km/h:** aparece o efeito luminoso à frente.
- **88 km/h:** dispara a viagem quando o sistema está preparado, com transição e recriação do mundo no outro estilo.
- Após a chegada, os efeitos da viagem anterior são desligados; existe intervalo de recuperação antes de outra viagem.

### Fenda e Upside Down

- Fenda posicionada junto à parede de um beco, com vermelho vivo e borda escura que desaparece em transparência.
- Cada aparição dura **60 segundos de simulação**, equivalentes a uma hora do jogo.
- Diminui lentamente; aos 59 segundos está bem pequena, ainda atravessável. Aos 60, deixa de aceitar travessia e desaparece em um breve fade-out.
- Depois muda de beco. Menus que pausam a simulação também pausam esse relógio.
- A travessia leva ao **Upside Down**: cidade escura e dessaturada, horário às 03:00 e atmosfera própria.
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
  - `radios/Upside Down/*.mp3` → trilha do Upside Down
  - `radios/Point Haze/*.mp3` → trilha de Point Haze
- **Trilhas de mundo (OST):** pastas chamadas `Synthwave`, `Upside Down` (ou `Invertido`), `Point Haze` e `Moderno`. Elas aparecem na roda só dentro do mundo correspondente e são sintonizadas sozinhas ao entrar nele. Também tocam a pé, a 60% do volume. Ao sair do mundo, o rádio volta para a rádio que tocava antes.
- A roda do rádio mostra apenas o nome de cada rádio: 1 pasta, 1 rádio; 2 pastas, 2 rádios. Q rápido (ou a roda do mouse no carro) troca de rádio.
- **Pular música:** `.` / `,` no teclado, ↑ no controle ou o botão MÚSICA no celular. A troca é dentro da rádio atual.
- A cada sessão, a ordem das músicas de cada rádio é embaralhada e a rádio começa numa música sorteada, sempre do início da faixa. Ao terminar uma faixa, toca a próxima da mesma rádio; arquivo com erro é pulado. **Trocar de carro mantém a música em andamento.**
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
- Estado relacionado à fenda e ao Upside Down.

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
