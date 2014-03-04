Validador de números telefônicos brasileiros para Yii 1.x
=========================================================

Esta extensão é um validador de números telefônicos brasileiros através da utilização de expressões regulares. Podem ser validados somente números móveis (celulares) ou qualquer outro tipo de número telefônico, desde que o mesmo contenha o respectivo DDD. 

A extensão pode ainda validar números com ou sem máscara, sendo que caso contenha máscara, a mesma deve seguir o padrão: (99) 9999-9999 ou (99) 99999-9999, caso o telefone seja móvel e contenha o nono dígito.

A extensão já está preparada para validação de números de telefone móvel que contenha o nono dígito para os seguintes DDDs: 11, 12, 13, 14, 15, 16, 17, 18, 19, 21, 22, 24, 27 e 28.

##Requisitos

Esta extensão requer a versão 1.1 ou superior do Yii.

Testes foram realizados somente na versão 1.1.x.

##Uso

Copie o arquivo IWPhoneNumberValidator.php para o diretório 

~~~
protected/extensions/validators/
~~~

No método rules() da sua classe de modelo, você deve incluir a chamada da extensão, da seguinte maneira:

~~~
public function rules()
{
  return array(
    ....,
    array('telefone', 'ext.IWPhoneNumberValidator'),
    ....,
    );
}
~~~

Por padrão a extensão valida qualquer número de telefone, caso queira validar somente números de telefones móveis (celulares), adicione o seguinte parâmetro.

~~~
public function rules()
{
  return array(
    ....,
    array('telefone', 'ext.IWPhoneNumberValidator', 'onlyMobileNumbers' => TRUE),
    ....,
    );
}
~~~

Por padrão a extensão aceita campos vazios ou nulos como verdadeiros, caso deseje remover esta aceitação, adicione o seguinte parâmetro:

~~~
public function rules()
{
  return array(
    ....,
    array('telefone', 'ext.IWPhoneNumberValidator', 'allowEmpty' => FALSE),
    ....,
    );
}
~~~

A extensão por padrão, também valida números de telefone sem máscaras, caso queira considerar a máscara na validação do número, adicione o seguinte parâmetro:

~~~
public function rules()
{
  return array(
    ....,
    array('telefone', 'ext.IWPhoneNumberValidator', 'validateWithMask' => TRUE),
    ....,
    );
}
~~~


> Vale lembrar que o padrão de máscara aceito é: (99) 9999-9999 ou (99) 99999-9999 quando o número for de um telefone móvel com o nono dígito. Caso deseje alterar a expressão regular de validação da máscara, altere os atributos phoneWithMaskPattern e mobilePhoneWithMaskPattern.
 

Por último a mensagem exibida ao usuário pode ser customizada através da adição do parâmetro customMessage, da seguinte maneira.

~~~
public function rules()
{
  return array(
    ....,
    array('telefone', 'ext.IWPhoneNumberValidator', 'onlyMobileNumbers' => TRUE, 'customMessage' => 'O campo "{attribute}" não é um número de celular válido.'),
    ....,
    );
}
~~~

##Créditos

Os créditos pelas expressões regulares são do Fausto Gonçalves Cintra. 
Maiores informações no endereço: http://goncin.wordpress.com/2010/08/30/validando-numeros-de-telefone-com-expressoes-regulares/

##Versões

28/10/2011 - 1.0 - Versão inicial do validador.

04/03/2014 - 1.1 - Inclusão de validação de nono dígito.

##Contatos

Ivan Wilhelm

E-mail: ivan.whm@me.com

Twitter: @ivanwhm

Skype: ivan.whm

Outros projetos: https://github.com/ivanwhm