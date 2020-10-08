## Entrada da ETAPA 01 - Conversão inicial

Nesta etapa apenas foram sanitizados os arquivos XML originais (pasta [recebidoOriginal](../../recebidoOriginal)) e convertidos para XML correto, em UTF-8 e com conteúdos em texto (não `CDATA`).

1. Conversão de *encoding*: foi necessária uma etapa de conversão padrão do *XML encoding* original "iso-8859-1" para "UTF-8". Tecnicamente a conversão fica mais simples se no mesmo processo os blocos `CDATA` forem expandidos para texto (e tratando eventuais tags HTML como texto).  Todo o processo pode ser reproduzido rodando-se o script `proc.php etapa1a`, conforme dump abaixo  que resultou no  [*commit* `a34c490`](https://github.com/ppKrauss/SBPqO-2020/commit/a34c49006f6a71b5b1f8423a508115edd85dae92).

    1.1. Conversão "iso-8859-1" para "UTF-8", conforme padronizado por [libxml](http://www.xmlsoft.org/html/libxml-encoding.html) (usando [iconv](https://www.gnu.org/software/libiconv/)) no [DOMDocument PHP](https://www.php.net/manual/en/book.dom.php).

    1.2. Expansão dos blocos `CDATA` conforme [padrão SimpleXML do PHP](https://www.php.net/manual/en/book.simplexml.php) (invoca [parser NOCDATA libxml](http://www.xmlsoft.org/html/libxml-parser.html)) e seu uso no script.

2. etapa 01b: Convertendo residuos XHTML do CDATA, ver [commit/98fed58](https://github.com/ppKrauss/SBPqO-2020/commit/98fed587f63ea88f826eee9ce7c2f89a6c4afb93)

3. etapa 01c: ver dump abaixo.

-----

## dump da etapa 01c

```
 -- etapa01c - Convertendo (e contando) entidades numéricas dos XMLs originais --
	AO.xml:
		VERIFICAR: &#61502; &#8594; &#1181; &#1180; &#64257;
		TOTAL 179 entities.
	COL.xml:
		TOTAL 11 entities.
	DMG.xml:
		TOTAL 10 entities.
	FC.xml:
		VERIFICAR: &#9650;
		TOTAL 23 entities.
	HA.xml:
		TOTAL 18 entities.
	LH.xml:
		TOTAL 16 entities.
	PDI.xml:
		TOTAL 2 entities.
	PE.xml:
		TOTAL 9 entities.
	PI.xml:
		VERIFICAR: &#8239; &#9078; &#611; &#120572; &#8237; &#8236; &#1050; &#65039; &#8304; &#7521; &#64257; &#8539; &#8260;
		TOTAL 590 entities.
	PN.xml:
		VERIFICAR: &#8322; &#120572; &#120514; &#8706; &#632; &#7506; &#119867; &#119874; &#119877; &#8314; &#769; &#42889; &#65039; &#8594; &#9078; &#8451; &#409;
		TOTAL 1028 entities.
	PO.xml:
		TOTAL 6 entities.
	RS.xml:
		TOTAL 27 entities.
	TCC.xml:
		TOTAL 48 entities.
 chr(257)=ā *5
 chr(333)=ō *1
 chr(409)=ƙ *1
 chr(611)=ɣ *1
 chr(632)=ɸ *1
 chr(706)=˂ *25
 chr(707)=˃ *6
 chr(730)=˚ *3
 chr(769)=́ *1
 chr(914)=Β *2
 chr(916)=Δ *239
 chr(917)=Ε *1
 chr(937)=Ω *1
 chr(945)=α *435
 chr(946)=β *159
 chr(947)=γ *12
 chr(948)=δ *2
 chr(949)=ε *2
 chr(951)=η *2
 chr(952)=θ *6
 chr(954)=κ *6
 chr(955)=λ *2
 chr(956)=μ *148
 chr(961)=ρ *7
 chr(963)=σ *15
 chr(964)=τ *4
 chr(967)=χ *11
 chr(1050)=К *1
 chr(1180)=Ҝ *1
 chr(1181)=ҝ *2
 chr(7506)=ᵒ *2
 chr(7521)=ᵡ *1
 chr(8202)=  *2
 chr(8203)=​ *28
 chr(8208)=‐ *5
 chr(8236)=‬ *61
 chr(8237)=‭ *61
 chr(8239)=  *1
 chr(8260)=⁄ *2
 chr(8304)=⁰ *1
 chr(8314)=⁺ *2
 chr(8322)=₂ *2
 chr(8451)=℃ *1
 chr(8539)=⅛ *1
 chr(8594)=→ *4
 chr(8706)=∂ *2
 chr(8710)=∆ *52
 chr(8722)=− *1
 chr(8725)=∕ *1
 chr(8773)=≅ *3
 chr(8776)=≈ *3
 chr(8804)=≤ *118
 chr(8805)=≥ *95
 chr(9078)=⍶ *2
 chr(9082)=⍺ *4
 chr(9650)=▲ *6
 chr(42889)=꞉ *1
 chr(61502)= *1
 chr(64257)=ﬁ *2
 chr(65039)=️ *10
 chr(119867)=𝐻 *1
 chr(119874)=𝑂 *1
 chr(119877)=𝑅 *1
 chr(120514)=𝛂 *1
 chr(120572)=𝛼 *13
```
