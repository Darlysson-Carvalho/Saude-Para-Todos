Saúde para Todos

Site para facilitar a localização e o atendimento em unidades de saúde (UBS, PSF e hospitais públicos e privados), com busca, mapa, agendamento e uma área para profissionais.

Status: protótipo de demonstração. Os dados (unidades, médicos, salas, datas e pacientes) são fictícios. Nada é enviado nem salvo.

Restrição do projeto

O site usa somente HTML5 e CSS3. Não há JavaScript, frameworks, Python, Java nem qualquer back-end.

Tecnologias
Item	Uso
HTML5	Estrutura e conteúdo das páginas
CSS3	Visual e comportamento: filtros, seleção, resumo e animações
Google Fonts	Fonte Plus Jakarta Sans (opcional; sem ela usa a fonte do sistema)
OpenStreetMap	Mapas incorporados (<iframe>)
Google Maps	Link de rota ("Como chegar")

Recursos de CSS usados no lugar de JavaScript:

:has(), :checked, :valid e :target para reagir às escolhas do usuário.
Contadores de CSS (counter-increment) para contar resultados filtrados.
::after { content: "..." } para repetir as escolhas no painel de resumo.
<details> para abrir e fechar o FAQ e as fichas dos pacientes.
@supports (animation-timeline: view()) para revelar seções ao rolar.
prefers-reduced-motion para respeitar quem prefere menos movimento.
Estrutura de pastas
site/
├── README.md
├── html/
│   ├── index.html                  Página inicial
│   ├── cadastro.html               Cadastro do paciente
│   ├── login.html                  Login do paciente
│   ├── profissional.html           Escolha de acesso do profissional
│   ├── cadastro_profissional.html  Cadastro do profissional
│   ├── login_profissional.html     Login do profissional
│   ├── inicial_profissional.html   Área do profissional
│   ├── plataforma.html             Guia de uso e busca de unidades
│   ├── localizacao.html            Lista + mapa + detalhes
│   ├── atendimento.html            Agendamento + Meu Local de Atendimento
│   ├── contato.html
│   ├── privacidade.html
│   └── termos.html
├── css/
│   ├── base.css                    Variáveis, reset, botões, cabeçalho, rodapé
│   ├── componentes.css             Abas, tags, chips, tabelas (plataforma, mapa, agendamento, profissional)
│   └── <página>.css                Um arquivo por página
└── img/                            Imagens (ex.: equipemedica.png) — pasta do projeto

Ordem de carregamento do CSS: base.css → componentes.css (quando usado) → CSS da página.

Como executar

Não há instalação nem build.

Baixe ou clone o projeto.
Abra html/index.html no navegador (duplo clique).
Use um navegador atual. As regras com :has() exigem Chrome, Edge, Safari ou Firefox em versão recente.

Os mapas precisam de internet.

Páginas e regras de negócio
Acesso
Há 3 formas de entrar: criar cadastro, fazer login ou continuar sem cadastro.
A área do profissional é separada, com cadastro e login próprios.
Cadastro do profissional: nome, e-mail, CPF, registro profissional (CRM, COREN, CRF…) e senha (mínimo de 8 caracteres).
Visitante sem conta pode buscar unidades, ver o mapa e simular um agendamento.
Busca de unidades (plataforma.html)
Tipos de unidade: UBS, PSF, hospital público e hospital privado.
Tipo de atendimento: SUS ou plano de saúde. Uma unidade pode atender os dois.
Os filtros de atendimento, tipo e especialidade se combinam entre si.
Cada unidade mostra endereço, horários e especialidades, com os botões Ver no mapa e Agendar.
Inclui guia de uso em 4 passos, glossário (UBS, PSF, hospitais) e aviso de emergência (SAMU 192).
Mapa (localizacao.html)
Tela dividida: lista filtrável à esquerda, mapa e detalhes à direita.
A unidade escolhida mostra mapa, endereço, rota, horários e disponibilidade dos médicos.
A seleção usa o endereço da página (#u-1 a #u-5), então o link "Ver no mapa" abre direto a unidade certa.
Agendamento (atendimento.html)
Obrigatórios: nome, SUS ou plano, unidade, especialidade, data e horário. CPF e Cartão SUS são opcionais.
A escolha de SUS ou plano filtra as unidades compatíveis.
As especialidades mudam conforme a unidade.
Horários ocupados aparecem riscados e não podem ser escolhidos.
O painel Meu Local de Atendimento mostra status, unidade, endereço, sala, especialidade, data, horário, mapa e rota.
Status do agendamento: aguardando preenchimento → pronto para confirmar → confirmado (demonstração).
Área do profissional (inicial_profissional.html)
Agenda do dia com os pacientes, que abrem para mostrar motivo e observação da recepção.
Filtros por situação (aguardando, em atendimento, concluído) e por SUS ou plano, com contagem automática.
Local de atendimento, horários da semana e lista de conferência antes da consulta.
Design
Paleta: azul (--blue-500: #2b8bd8) e verde-água (--teal-500: #19b6a6), com tema azul sólido para o profissional (body.tema-pro).
Variáveis em base.css: cores, gradientes, raios, sombras e fonte.
Responsivo: funciona em computador, tablet e celular.
Acessibilidade: link "pular para o conteúdo", foco visível, textos alternativos, aria-label e aria-current nas abas.
Como adicionar uma unidade real
Em plataforma.html, copie um bloco <article class="unit"> e ajuste nome, endereço, horários, especialidades e os atributos data-atend, data-tipo e data-esp.
Em localizacao.html, copie um item da lista (<li class="unit-item">) e um bloco <article class="detail" id="u-N">. Troque as coordenadas do mapa e da rota.
Em atendimento.html, copie um cartão .uni, o grupo de especialidades correspondente, o mapa .pm-N e a rota .rota-N. Depois acrescente as regras da unidade em css/atendimento.css, seguindo o padrão das existentes.

Use sempre dados oficiais e confirmados. Os horários e as especialidades do site devem ser conferidos com a unidade.

Limitações atuais
Os dados são fictícios e as datas de agendamento são fixas (16/11 a 23/11/2026).
Nada é salvo. Ao recarregar a página, tudo volta ao início.
Não há login real, validação de senha nem confirmação oficial pela unidade.
As senhas dos formulários não têm name, para não irem na URL. Ao ligar um servidor, use method="post" e name="senha".
Cada nova unidade exige editar HTML e CSS à mão, porque não há banco de dados.
Próximos passos sugeridos

Estes itens exigem um servidor e fogem da restrição atual de só HTML e CSS:

Back-end com banco de dados (pacientes, unidades, profissionais, agendamentos).
Login e senha de verdade, com proteção de dados conforme a LGPD.
Confirmação do agendamento pela unidade, com protocolo e notificações.
Disponibilidade de horários em tempo real.
Integração com dados oficiais de estabelecimentos de saúde (CNES).
Textos reais das páginas de privacidade e termos de uso.
Autoria

Projeto de Darlysson, estudante de Ciência da Computação no UNIPÊ (João Pessoa, PB).