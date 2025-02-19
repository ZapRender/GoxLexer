En mi codigo tuve una fuerte influencia en el capitulo de Scanning del libro: CRAFTING INTERPRETERS

El primer obstaculo que me encontre fue el hecho de que el capitulo tuviera explicación en Java. Sin embargo no fue un problema tan grande, solo fue interpretar a mi manera el codigo.

Según el capitulo, utiliza un enum class para definir los tipos de tokens, itentando seguir este enfoque, tambien utilice un enum class, sin embargo me vi obligado a dejarlo solamente para la organización, ya que me tocó usar diccionarios para poder mapear los tokens de manera mas precisa y rapida.

En el archivo de TokenType.py tengo definido 3 diccionarios.

SINGLE_CHAR_TOKENS: Este diccionario define los tokens individuales, los que son conformados por solo un caracter.

TOKEN_LITERALS: Este dicionario abarca los literales y los identificadores

KEYWORDS: Este diccionario es donde se definen todas las palabras clave que se van a utilizar en el lexico de Gox.

Antes de continuar con el resto del scanner, creé el archivo lexer.py en donde está ubicada la clase nombrada como Gox, la que utilizo para iniciar con el scaneo.

En esta clase se define la funcion _runFile, esta tiene como objetivo abrir el archivo en modo lectura binaria para así leer el contenido en bytes y decodificarlo en una cadena de caracteres. Aunque al principio el leer el contenido en bytes era por seguir el enfoque del capitulo, investigando me di cuenta que la ventaja es que este modo se asegura de leer los datos exactamente como se encuentran en el archivo, sin embargo he de decir que hay foros en los que se dice que es mejor utilizar rb solo para archivos diferentes a textos.

Mientras hacia las unit test en la parte de numeros, me di cuenta que la prueba no estaba pasando, analizando el porque, resultaba en que
#el numero negativo no lo estaba tomando como un entero, estaba tomando el '-' como un token, por lo que tuve que modificar el codigo para que
#pueda tomar numeros negativos como enteros.
cuando habia dado por terminado el scanner, me di cuenta que el scanner estaba dividiendo las cadenas de texto caracter por caracter, asi que me toco modificarlo para que tomara todas las cadenas de caracteres como un solo lexeme