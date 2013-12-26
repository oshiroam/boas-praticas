Boas Práticas
==============

## Geral
* Vai fazer um CRUD? cria tudo de uma vez.. não fica enrolando pra criar os testes..
* Ta criando método novo? Já cria a referência nos testes.. pelo menos quando rodar o teste já vai mostrar a baixa procentagem..
* Use o Localize, Unlocalize se tiver. Já que tem usa, não fica fazendo strrepalce..
* Cara.. use [callBacks](http://book.cakephp.org/2.0/en/models/callback-methods.html)..
* Comentário de método é grudado na margem, de classe tbem.. Dá uma olhada no padrão do cakphp.
* Se você achou que seu código ta uma ruim de entender, coloca um comentário nele..
* Ainda não sei se é uma boa fazer isso $this->__setFormData(); Se só o *add()* e o *edit()* vão usar os dados, acho que é uma boa usar ele.
	*  Para coisas bem especificas, algo que o *beforeRender()* não precise fazer.
* No Form->input, se *options* então *empty*.
* Use else com cuidado, no geral, não precisa!
* Padronize o nome/tipo dos campos por TODO o projeto.. Quando vpcê ler uma variável vai saber o que é não importa onde esteja.
* Use *// TODO descrição do problema* Use uma descrição rápida e direta na primeira linha. No findal all ja é possçĩvel saber do que se trata o *TODO*

## Sobre Controllers
* Controller não salva, nãp carrega muitos dados não faz muita coisa.
* Faça verificação de empty do request->data no controller.. você já faz isso antes de mandar pro modelo.. não precisa verificar de novo no modelo.
* Prefixo *ajax* em métodos ajax.. ok?
    Ex:
```
public function ajaxLalala()
{
		$this->request->onlyAllow(['ajax']);

		$this->set('data', $data);
		$this->set('_serialize', 'data');
}
```
* Sobre [$this->request->onlyAllow(string|array $methods)](http://api.cakephp.org/2.4/class-CakeRequest.html#_onlyAllow).
* Usar $this->request->onlyAllow() somente para métodos que não tem view.

## Sobre Models
* Modelo faz a mágica toda, ele resolver QUASE tudo pra você.
* Disparar evento no modelo, não salva dados que deveriam ser de outro modelo.
	* Ex: Model A (só salva coisas do model A) -> evento -> Model B (só salva coisas do model B)
* Se você precisa salvar model, evento e depois o model de novo, você precisa rever a associação.
* Se seu campo data não precisa ser muito especifico, use *type date*, senão é *datetime* e cuide disso.
* Vou usar só *type number* pra *float*, azar..
* Mantenha o schema do fixture e do model sempre atualizados.

## Sobre Views
* View, só mostra msm, no muito faz umas contas de somar..

## Sobre Formatação de códigos
* Nome de método protected começa com 1 _
	* Ex: potected function _methodProtected(){}
* Código de debug grudado na margem e com separação de pelomenos uma linha acima e abaixo, ajuda pra muito no find all..
	*  Serve também pra pr(), console.log(), die(), die; e outros.
* Usa espaço e não tab, configure isso no seu editor.
