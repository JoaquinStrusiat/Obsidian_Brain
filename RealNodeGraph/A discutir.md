### Relaciones:
Las relaciones no tienen dueño (`owner`), son un contrato bi-direccional entre dos entidades, ambas entidades necesitan verse entre si para poder negociar esta relación
1) Para poder crear una relación se deben cumplir las siguientes condiciones:
	1) El `from` de la relación puede ser:
		- El mismo usuario que quiere crear la relación
		- Un objeto del cual se es dueño  (`owner`)
		- Tener acceso de crear relaciones del tipo entrante sobre este o objeto
	2) El `to` tiene que ser visible por el creador de la relación
		- Ser dueño del objeto
		- Que sea público
		- Un documento al que me dieron acceso

### Uso funcional (relación):

Define el **rol funcional actual** del objeto en el sistema (depende del contexto).

El uso funcional de un objeto determina el uso que se le puede dar a un objeto en un determinado contexto, independientemente del tipo. Por ejemplo, un mismo objeto de tipo computadora puede ser un activo (`asset`) o un producto (`producto`) en función del uso que se le de:

Lo planteo como una relación ya que de por medio se podría anexar metadatos o información relacionada:

**Lista de Roles Funcionales: **

- functional_role
	- product: Bien destinado a la venta a un cliente final o distribuidor.
	- asset: Bien usado internamente por la empresa para sus operaciones.
	- rental: Bien que se alquila a terceros.
	- consumable: Bien que se usa y se agota.

