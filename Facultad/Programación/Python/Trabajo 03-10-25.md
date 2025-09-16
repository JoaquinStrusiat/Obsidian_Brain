``` python
class Galleta:
    def __init__(self, nombre, forma):
        self.nombre = nombre
        self.forma = forma

    def hornear(self):
        print(f'{self.nombre} se hornea con forma {self.forma}')
        
    def describir(self):
        return f'{self.nombre} tiene forma de {self.forma}'


class GalletaRellena(Galleta):
    def __init__(self, nombre, forma, relleno):
        super().__init__(nombre, forma)
        self.relleno = relleno

    def hornear(self):
        super().hornear()
        print(f'Rellena con {self.relleno}')


class Almacen:
    def __init__(self, nombre):
        self.nombre = nombre
        self.inventario = []

    def recibir_galleta(self, galleta):
        self.inventario.append(galleta)
        print(f'{galleta.nombre} enviada al almacén {self.nombre}')
        
    def mostrar_inventario(self):
        print(f"Inventario del almacén {self.nombre}:")
        for i, galleta in enumerate(self.inventario, 1):
            print(f"{i}. {galleta.nombre} - Forma: {galleta.forma}")
            # Si es GalletaRellena, mostrar también el relleno
            if hasattr(galleta, 'relleno'):
                print(f"   Relleno: {galleta.relleno}")

# galleta4 = GalletaRellena('Galleta Rellena', 'círculo', 'dulce de leche')
# galleta4.hornear()
        
        

galletas = [
    Galleta('Estrella', 'estrella'),
    Galleta('Árbol', 'árbol'),
    Galleta('Corazón', 'corazón'),
    Galleta('Luna', 'Luna')
]

for galleta in galletas:
    print(galleta.describir())


almacen_norte = Almacen('Norte')
almacen_sur = Almacen('Sur')

almacen_norte.recibir_galleta(galletas[0])
almacen_norte.recibir_galleta(galletas[2])
almacen_norte.recibir_galleta(galletas[3])
almacen_sur.recibir_galleta(galletas[1])

print("<<<<<<<<<<<<<<<<<<<<<<<<<<<<<INVENTARIO DE GALLETAS >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>");

almacen_norte.mostrar_inventario()

```
