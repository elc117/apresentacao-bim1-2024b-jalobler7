# Programação Funcional na prática
Analisando o código do jogo da forca


# Panorama geral
Este código em Haskell cria um servidor web usando o framework Scotty, com endpoints para realizar operações relacionadas a um jogo de forca. Vamos passar pelas principais funções e módulos envolvidos, explicando o que cada parte faz.

# Analisando as funções implementadas 

## sorteiaEsalva :: IO ():

Lê o conteúdo do arquivo texto.txt, onde há uma lista de palavras separadas por vírgulas.
Separa as palavras, sorteia uma delas aleatoriamente, e a salva em um arquivo palavraSorteada.txt.

## lerArquivo :: FilePath -> IO String:
Lê o conteúdo de um arquivo e retorna uma String. É usada para ler arquivos como texto.txt e palavraSorteada.txt.

## separaPalavra :: String -> [String]:
Usa splitOn para dividir a string em uma lista de palavras, usando vírgulas como delimitador

## sorteia :: [a] -> IO a:
Sorteia um item de uma lista, gerando um índice aleatório e retornando o elemento correspondente.

## salvaPalavra :: String -> IO ():
Salva a palavra sorteada no arquivo palavraSorteada.txt.

## retornaPalavraArq :: IO String:
Lê a palavra salva no arquivo palavraSorteada.txt e a retorna.

## temLetra :: Char -> IO String:
Verifica se uma letra fornecida pelo usuário existe na palavra sorteada. Se sim, retorna "Letra Certa"; se não, incrementa o contador de vidas perdidas e retorna "Letra Errada".

## VerificaLetra :: String -> Char -> Bool:
Verifica se uma determinada letra está presente na palavra.

## perdeVida :: IO Int:
Lê o número de vidas perdidas do arquivo vidas.txt, incrementa o número, e salva o novo valor no mesmo arquivo. Retorna o novo número de vidas.

## verificaSePerdeu :: IO String:
Verifica se o jogador perdeu o jogo (se o número de vidas é maior ou igual a 6). Caso contrário, retorna quantas vidas restam.

## leArqVida :: IO Int:
Lê o arquivo vidas.txt, converte o conteúdo para um número inteiro e o retorna.

## zeraTudo :: IO ():
Zera o número de vidas, salvando o valor 0 no arquivo vidas.txt.

# Paradigmas da programação funcional encontrados no programa
## 1. Funções Puramente Funcionais
Funções puramente funcionais são aquelas que, dado o mesmo input, sempre produzem o mesmo output, sem efeitos colaterais. No código, algumas funções seguem essa filosofia, como:

separaPalavra: É uma função que toma uma string e a divide em uma lista de strings. Dado um input, ela sempre retornará o mesmo resultado sem causar nenhum efeito colateral, como modificar variáveis externas ou interagir com I/O.

verificaLetra: Verifica se uma letra está presente em uma palavra. Também não realiza efeitos colaterais, apenas retorna um booleano.

Essas funções são puramente funcionais, o que é uma característica fundamental da programação funcional.

## 2. Uso de Imutabilidade
No paradigma funcional, os dados são imutáveis. Ou seja, uma vez que uma estrutura de dados é criada, ela não pode ser alterada. Embora o código interaja com I/O e arquivos, as estruturas de dados internas do programa (listas, strings, etc.) são tratadas de maneira imutável:

Listas: As listas, como na função separaPalavra, não são modificadas diretamente. Em vez disso, sempre que uma operação é realizada, uma nova lista é criada.

sorteia: A função que realiza o sorteio não modifica a lista original, apenas retorna um valor selecionado, mantendo a imutabilidade da lista.

## 3.Composição de Funções
A programação funcional valoriza a composição de funções menores para formar soluções mais complexas. Embora o código não tenha explicitamente composição usando o operador (.), é possível observar a utilização de funções pequenas e reutilizáveis. Por exemplo:

A função sorteiaEsalva compõe várias funções para formar um comportamento maior: ************* terminar

Aqui, a função lê o arquivo, separa as palavras, sorteia uma e depois a salva. Cada função executa uma tarefa simples e essas funções são combinadas para formar a lógica completa.

