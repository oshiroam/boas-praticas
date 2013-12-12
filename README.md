Boas Práticas
==============

## Geral
* Vai fazer um CRUD? cria tudo de uma vez.. não fica enrolando pra criar os testes..
* Ta criando método novo? Já cria a referência nos testes.. pelo menos quando rodar o teste já vai mostrar a baixa procentagem..
* Usa a porra do Localize, Unlocalize se tiver. já que tem usa, não fica fazendo strrepalce..
* Cara.. use [callBacks](http://book.cakephp.org/2.0/en/models/callback-methods.html)..
* Comentário de método é grudado na margem, de classe tbem..
* Se você achou que seu código ta uma merda de entender, coloca um comentário nele..
* Ainda não sei se é uma boa fazer isso $this->__setFormData(); Se só o add e o edit vão usar os dados, acho que é uma boa usar ele.
        + Para coisas bem especificas, algo que o beforeRender não precise fazer.
* No Form->input, se 'options' então 'empty'.
* Use else com cuidado, no geral, não precisa!

## Sobre Controllers
    * Controller não salva, nãp carrega muitos dados não faz muita coisa.
    * Faça verificação de empty do request->data no controller.. você já faz isso antes de mandar pro modelo.. não precisa verificar de novo no modelo.
    * Prefixo ajax em métodos ajax.. ok?
        Ex:
            public function ajaxLalala()
            {
                $this->request->onlyAllow(['ajax']);

                ...

                $this->set('data', $data);
                $this->set('_serialize', 'data');
            }
    * Sobre [$this->request->onlyAllow(string|array $methods)](http://api.cakephp.org/2.4/class-CakeRequest.html#_onlyAllow).

## Sobre Models
    * Modelo faz a merda toda, ele se fode pra resolver QUASE tudo.
    * Disparar evento no modelo, não salva dados que deveriam ser de outro modelo.
        Ex: Model A (só salva coisas do model A) -> evento -> Model B (só salva coisas do model B)
    * Se você precisa salvar model, evento e depois o model de novo, você precisa rever a associação.
    * Se seu campo data não precisa ser muito especifico, use type date, senão é datetime e cuide disso.
    * Vou usar só type number pra float, azar..
    * Mantenha o fixture e o model sempre atualizados.

## Sobre Views
    - View, só mostra msm, no muito faz umas contas de somar..

## Sobre Formatação de códigos
    * Nome de método protected começa com 2 __
    * Nome de método private começa com 1 _
    * Código de debug grudado na margem e com separação de duas linhas acima e abaixo, ajuda pra caralho no find all..
    * Usa espaço e não tab.
