## Entrada da ETAPA 01 - Conversão inicial

Nesta etapa apenas foram sanitizados os arquivos XML originais (pasta [recebidoOriginal](../../recebidoOriginal)) e convertidos para XML correto, em UTF-8 e com conteúdos em texto (não `CDATA`).

1. Conversão de *encoding*: foi necessária uma etapa de conversão padrão do *XML encoding* original "iso-8859-1" para "UTF-8". Tecnicamente a conversão fica mais simples se no mesmo processo os blocos `CDATA` forem expandidos para texto (e tratando eventuais tags HTML como texto).  Todo o processo pode ser reproduzido rodando-se o script `proc.php etapa1a`, conforme dump abaixo  que resultou no  [*commit* `a34c490`](https://github.com/ppKrauss/SBPqO-2020/commit/a34c49006f6a71b5b1f8423a508115edd85dae92).

    1.1. Conversão "iso-8859-1" para "UTF-8", conforme padronizado por [libxml](http://www.xmlsoft.org/html/libxml-encoding.html) (usando [iconv](https://www.gnu.org/software/libiconv/)) no [DOMDocument PHP](https://www.php.net/manual/en/book.dom.php).

    1.2. Expansão dos blocos `CDATA` conforme [padrão SimpleXML do PHP](https://www.php.net/manual/en/book.simplexml.php) (invoca [parser NOCDATA libxml](http://www.xmlsoft.org/html/libxml-parser.html)) e seu uso no script.
