para o desenvolvimento deste algoritmo tentei seguir da seguinte forma:
- criar uma matriz 9x9 para alocacao dos numeros
- dividir a 9x9 em matriz em 3x3, para que seja possivel atribuir os valores corretamente.
- para a primeira matriz 3x3 foi alocado numeros de 1 a 9 randomicamente.
- a partir destes numeros foi inserido numeros nas matrizes 3x3 de forma a verificar linha, coluna e valores da matriz 3x3 para que nao se repitam.
- quando se insere os numeros procurei adicionar de forma crescente ,ou seja, cada vez que inserir um numero volto para o menor numero nao iserido e tento iserir na matriz sempre verificando.
- depois de inserir todos os numeros temos a tabela do sudoku, agora sera neccessario esconder alguns numeros para gerar o desafio, para isto pretendo fazer da seguinte forma, a cada numero retirado matriz verifico se este numero continua sendo um solitario(na referencia explica oque e um numero solitario), se continua retiro mais um ate que chegue a quantidade de numeros que deseja ter no jogo.
- No jogo e normal ter mais de um solitario sendo assim aunica restricao seria que pelo menos deve se ter um solitario para que o jogo seja de solucao unica.
