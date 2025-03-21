# Validação de inscrições estaduais

---------

## # Dada a descontinuidade do projeto pela Gamasoft, estamos assumindo a sua continuidade com total adesão à licença MIT.
## IE
### Validação de [inscrições estaduais](http://pt.wikipedia.org/wiki/Inscri%C3%A7%C3%A3o_Estadual "Inscrição Estadual no Wikipedia") em JavaScript (browser e node.js)
Validações implementadas de acordo com o [manual do Sintegra](http://www.sintegra.gov.br/insc_est.html).


#### Node.js

Instalação:
```bash
npm install @printi/inscricao-estadual@1.0.3
```
Utilização:

```javascript
var ie = require("inscricaoestadual");
ie(inscricaoEstadual, uf);
```
#### Browser

Instalação: faça o download [aqui](https://github.com/Printi/inscricao-estadual/blob/main/ie.min.js) ou via bower:
Bower já está praticamente deprecated, não aceita mais novos registros de pacote, só conseguimos instalar agora pelo github
```bash
bower install --save git://github.com/Printi/inscricao-estadual.git#latest
```

Utilização:
```html
<script src="ie.min.js"></script>
<script>
    inscricaoEstadual('suaInscricaoEstadual', 'UF');
</script>
```

Utilização com AMD (RequireJS e afins):

```javascript
define(['vendor/inscricao-estadual/ie.min.js'], function(ie){
    ie('suaInscricaoEstadual', 'UF');
});
```

-----------------------------------------

#### ie(inscricaoEstadual[, uf])
 - `inscricaEstadual` uma string contendo o valor a ser validado ou um array de strings.
 Pode-se receber uma string com máscara, pois os separadores `[".", "-", "/", " "]` são desconsiderados para a validação.
 Caso seja passado o valor "isento" (independente de case maiúsculo ou minúsculo) é retornado `true`.

 - `uf` é opcional, mas se fornecida pode ser `""` (string vazia) ou deve ser uma string entre um dos valores

```javascript
["ac", "al", "ap", "am",
"ba", "ce", "df", "es",
"go", "ma", "mt", "ms",
"mg", "pa", "pb", "pr",
"pe", "pi", "rj", "rn",
"rs", "ro", "rr", "sc",
"sp", "se", "to"]
```
 No caso de ser string vazia ou não fornecida, a função `ie` retorna um array de estados nas quais esta inscrição estadual tem um valor válido, útil quando se tem uma inscrição estadual mas não se sabe a qual estado ela pertece, por exemplo:
```javascript
ie("012345679") === ["se", "pb", "am", "ro", "sc", "pi", "es", "mt", "to"];
```
 Quando o estado é fornecido, a validação é otimizada pois o valor da inscrição estadual é testada apenas contra a regra do estado especificado e a função retorna estritamente `true` ou `false`.

### Contribuindo

Faça um fork depois um pull request. Contribuições só são aceitas com testes unitários.

#### Testes

Para rodar os testes:
    npm install -g grunt-cli
    npm test

Todas as inscrições estaduais nos testes foram obtidas publicamente na internet.
Se você obteve uma validação falsa para uma inscrição estadual verdadeira, pesquise no site do [Sintegra](http://www.sintegra.gov.br/ "Sintegra") se de fato esta inscrição estadual existe e é valida, neste caso [abra uma notificação](https://github.com/Printi/inscricao-estadual/issues/new) aqui no GitHub para apurarmos o caso.

#### Minificando

Para minificar:
    npm install -g grunt-cli
	grunt minify

-----------------------------------------

#### Licença MIT
