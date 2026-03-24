# Checkpoint 1

## Descrição do projeto.
Este projeto é uma evolução de um app de navegação em Jetpack Compose, focado em aprender como enviar dados de uma tela para outra.

## Objetivo do projeto.
O objetivo foi implementar e entender a diferença entre parâmetros obrigatórios, opcionais e múltiplos parâmetros usando o Navigation Component.

### 1 - Passagem de parâmetros obrigatórios na tela de Perfil.
Para essa parte, eu atualizei a rota de perfil no NavHost para aceitar um argumento. Antes a rota era só "perfil", agora ela ficou como perfil/{nome}. Isso significa que o dado {nome} virou obrigatório; se eu tentar navegar sem ele, o app não encontra a tela e dá erro. No código da MainActivity, eu usei o it.arguments para pegar esse texto que vem da rota e passei ele para a função PerfilScreen. Na tela de perfil, eu mudei a função para receber essa String e usei o $ para mostrar o nome do usuário direto no texto da tela.

### 2 - Passagem de parâmetros opcionais na tela de Pedidos.
Aqui a lógica foi um pouco diferente porque usei parâmetros opcionais. Na rota da tela de pedidos, eu usei a interrogação (pedidos?cliente={cliente}), que funciona parecido com um link de site. A grande diferença é que eu precisei configurar um defaultValue (valor padrão) dentro do navArgument. Fiz isso para que, se eu navegar para a tela de pedidos sem passar nenhum nome, o app não trave e mostre um texto padrão, como "Cliente Genérico". Isso deixa a navegação muito mais segura.

### 3 - Inserção de valor em parâmetro opcional na tela Pedidos.
Para testar o parâmetro opcional, eu alterei o clique do botão lá na MenuScreen. Eu mudei o navController.navigate para enviar um valor específico, ficando assim: navController.navigate("pedidos?cliente=Cliente XPTO"). Com isso, eu consegui demonstrar que, quando eu passo um valor, ele sobrescreve aquele valor padrão que eu tinha configurado antes. Se eu não passasse nada no clique, ele usaria o padrão, mas como passei "Cliente XPTO", a tela de pedidos já abre com esse nome certinho.

### 4 - Passagem de múltiplos parâmetros entre telas.
Nesta última evolução, eu deixei a navegação mais complexa passando dois dados ao mesmo tempo: o nome e a idade. A rota ficou estruturada como perfil/{nome}/{idade}. O ponto mais importante aqui foi definir os tipos de dados usando o NavType. Eu configurei o nome como StringType e a idade como IntType. Na hora de recuperar esses dados na MainActivity, eu usei o getString e o getInt para garantir que o Android fizesse a conversão correta. Por fim, atualizei a PerfilScreen para exibir os dois dados juntos, mostrando uma frase completa com o nome e a idade da pessoa.